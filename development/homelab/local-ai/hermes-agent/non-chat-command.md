# ( non-chat ) Command

#### Check what you have installed and what needs fixed&#x20;

{% code overflow="wrap" %}
```
hermes doctor
```
{% endcode %}

{% code overflow="wrap" %}
```
hermes doctor --fix
```
{% endcode %}

#### Check and upgrade Hermes&#x20;

{% code overflow="wrap" %}
```
hermes upgrade
```
{% endcode %}

#### List skills

{% code overflow="wrap" %}
```
hermes skills list
```
{% endcode %}

#### Find a certain skills installed&#x20;

{% code overflow="wrap" %}
```
hermes skills list | grep -i "ping"
```
{% endcode %}

#### List tools

{% code overflow="wrap" %}
```
hermes tools list
```
{% endcode %}

#### Enable tools

{% code overflow="wrap" %}
```
hermes tools enable read_file 
```
{% endcode %}

* You can replace "read\_file" with "all" if you want to enable all

#### Resetup Hermes&#x20;

{% code overflow="wrap" %}
```
hermes setup
```
{% endcode %}
