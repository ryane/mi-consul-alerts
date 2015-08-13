consul-alerts
=========

A role that installs and configures [consul-alerts](https://github.com/AcalephStorage/consul-alerts). This is intended for usage on the [microservices-infrastructure](https://github.com/CiscoCloud/microservices-infrastructure) project.

Role Variables
--------------

### consul_alerts_notifiers

A list of key/value pairs that correspond to [consul-alerts notifiers](https://github.com/AcalephStorage/consul-alerts#notifiers) configuration.

    - { key: "log/enabled", value: "true" }

Dependencies
------------

This role depends on [consul-cli](https://github.com/CiscoCloud/consul-cli).

Example Playbook
----------------

This example shows how to enable slack notifications while disabling the text log file.

    - hosts: role=control
      vars:
        consul_alerts_notifiers:
        - { key: "log/enabled", value: "false" }
        - { key: "slack/enabled", value: "true" }
        - { key: "slack/cluster-name", value: "cluster-name" }
        - { key: "slack/url", value: "webhook_url" }
        - { key: "slack/channel", value: "#notifications" }
        - { key: "slack/detailed", value: "true" }
      roles:
        - mi-consul-alerts

Improvements
---------------

- [ ] Improve install (perhaps run in a docker container)

License
-------

Licensed under the Apache License, Version 2.0 (the "License").

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
