
# Pull profile
`Bullhorn Profiles` :arrow_right: `HrFlow.ai Profiles`

Writes a profile to Hrflow.ai source from Bullhorn via the API



## Action Parameters

| Field | Type | Default | Description |
| ----- | ---- | ------- | ----------- |
| `logics`  | `typing.List[typing.Callable[[typing.Dict], typing.Optional[typing.Dict]]]` | [] | List of logic functions |
| `format`  | `typing.Callable[[typing.Dict], typing.Dict]` | [`profile_format`](../connector.py#L267) | Formatting function |
| `read_mode`  | `str` | ReadMode.sync | If 'incremental' then `read_from` of the last run is given to Origin Warehouse during read. **The actual behavior depends on implementation of read**. In 'sync' mode `read_from` is neither fetched nor given to Origin Warehouse during read. |

## Source Parameters

| Field | Type | Default | Description |
| ----- | ---- | ------- | ----------- |
| `client_id` :red_circle: | `str` | None | Client identifier for Bullhorn |
| `client_secret` :red_circle: | `str` | None | Client secret identifier for Bullhorn |
| `password` :red_circle: | `str` | None | Passoword for Bullhorn login |
| `username` :red_circle: | `str` | None | Username for Bullhorn login |

## Destination Parameters

| Field | Type | Default | Description |
| ----- | ---- | ------- | ----------- |
| `api_secret` :red_circle: | `str` | None | X-API-KEY used to access HrFlow.ai API |
| `api_user` :red_circle: | `str` | None | X-USER-EMAIL used to access HrFlow.ai API |
| `source_key` :red_circle: | `str` | None | HrFlow.ai source key |
| `edit`  | `bool` | False | When enabled the profile must exist in the source |
| `only_edit_fields` :red_circle: | `str` | None | List of attributes to use for the edit operation e.g. ['tags', 'metadatas'] |

:red_circle: : *required*

## Example

```python
import logging
from hrflow_connectors import Bullhorn
from hrflow_connectors.core import ReadMode


logging.basicConfig(level=logging.INFO)


Bullhorn.pull_profile(
    workflow_id="some_string_identifier",
    action_parameters=dict(
        logics=[],
        format=lambda *args, **kwargs: None # Put your code logic here,
        read_mode=ReadMode.sync,
    ),
    origin_parameters=dict(
        client_id="your_client_id",
        client_secret="your_client_secret",
        password="your_password",
        username="your_username",
    ),
    target_parameters=dict(
        api_secret="your_api_secret",
        api_user="your_api_user",
        source_key="your_source_key",
        edit=False,
        only_edit_fields=***,
    )
)
```