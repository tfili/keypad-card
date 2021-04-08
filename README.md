Custom component for lovelace that guards a card behind a keypad. This can be useful for alarm systems that don't accept a code (eg. Abode) or for other cards that are sensitive.

![Screenshot](/images/keypad.jpeg)

## Config

| Name | Type | Description | Default
| ---- | ---- | ----------- | -------
| type | string | `custom:keypad-card` | **Required**
| card | object | The card to be guarded | **Required**
| code | number | The code that must be entered to see `card` | **Required**
| timeout | number | Number of seconds to show `card` before going back to the keypad (0 = _Show Forever_) | 0
| exemptions | list | Specify `user` parameter with the user ID or `username` with the username where keypad won't be shown | []

## Installation

### Step 1

Install `keypad-card` by copying `keypad-card.js` from this repo to `<config directory>/www/keypad-card/` on your Home Assistant instance.

**Example:**

```bash
mkdir <config directory>/www/keypad-card/
cd <config directory>/www/keypad-card/

wget https://raw.githubusercontent.com/tfili/keypad-card/master/keypad-card.js
```

### Step 2

Link `keypad-card` inside your `ui-lovelace.yaml`.

```yaml
resources:
  - url: /local/keypad-card/keypad-card.js?v=0
    type: module
```

Or add to `Configuration` -> `Lovelace Dashboards` -> `Resources`
![Add Resource](/images/add-resource.jpeg)

### Step 3

Add as custom card of a panel view in your `ui-lovelace.yaml` using `type: custom:keypad-card`

## Example
```yaml
type: custom:keypad-card
code: 12345
timeout: 10
exemptions:
  - user: b9f1f1d2a4ba406cba6739eece3ca1c6
  - username: John Doe
card:
  type: alarm-panel
  states:
    - arm_home
    - arm_away
  entity: alarm_control_panel.my_alarm
```

## Thanks

Thanks to all the people who have contributed!

[![contributors](https://contributors-img.web.app/image?repo=tfili/keypad-card)](https://github.com/tfili/keypad-card/graphs/contributors)
