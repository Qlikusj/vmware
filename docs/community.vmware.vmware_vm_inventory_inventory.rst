.. _community.vmware.vmware_vm_inventory_inventory:


************************************
community.vmware.vmware_vm_inventory
************************************

**VMware Guest inventory source**



.. contents::
   :local:
   :depth: 1


Synopsis
--------
- Get virtual machines as inventory hosts from VMware environment.
- Uses any file which ends with vmware.yml, vmware.yaml, vmware_vm_inventory.yml, or vmware_vm_inventory.yaml as a YAML configuration file.



Requirements
------------
The below requirements are needed on the local Ansible controller node that executes this inventory.

- Python >= 2.7
- PyVmomi
- requests >= 2.3
- vSphere Automation SDK - For tag feature
- vCloud Suite SDK - For tag feature


Parameters
----------

.. raw:: html

    <table  border=0 cellpadding=0 class="documentation-table">
        <tr>
            <th colspan="1">Parameter</th>
            <th>Choices/<font color="blue">Defaults</font></th>
                <th>Configuration</th>
            <th width="100%">Comments</th>
        </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>cache</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                    <td>
                            <div> ini entries:
                                    <p>[inventory]<br>cache = no</p>
                            </div>
                                <div>env:ANSIBLE_INVENTORY_CACHE</div>
                    </td>
                <td>
                        <div>Toggle to enable/disable the caching of the inventory&#x27;s source data, requires a cache plugin setup to work.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>cache_connection</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                    <td>
                            <div> ini entries:
                                    <p>[defaults]<br>fact_caching_connection = VALUE</p>
                                    <p>[inventory]<br>cache_connection = VALUE</p>
                            </div>
                                <div>env:ANSIBLE_CACHE_PLUGIN_CONNECTION</div>
                                <div>env:ANSIBLE_INVENTORY_CACHE_CONNECTION</div>
                    </td>
                <td>
                        <div>Cache connection data or path, read cache plugin documentation for specifics.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>cache_plugin</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">"memory"</div>
                </td>
                    <td>
                            <div> ini entries:
                                    <p>[defaults]<br>fact_caching = memory</p>
                                    <p>[inventory]<br>cache_plugin = memory</p>
                            </div>
                                <div>env:ANSIBLE_CACHE_PLUGIN</div>
                                <div>env:ANSIBLE_INVENTORY_CACHE_PLUGIN</div>
                    </td>
                <td>
                        <div>Cache plugin to use for the inventory&#x27;s source data.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>cache_prefix</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">-</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">"ansible_inventory_"</div>
                </td>
                    <td>
                            <div> ini entries:
                                    <p>[default]<br>fact_caching_prefix = ansible_inventory_</p>
                                    <p>[inventory]<br>cache_prefix = ansible_inventory_</p>
                            </div>
                                <div>env:ANSIBLE_CACHE_PLUGIN_PREFIX</div>
                                <div>env:ANSIBLE_INVENTORY_CACHE_PLUGIN_PREFIX</div>
                    </td>
                <td>
                        <div>Prefix to use for cache plugin files/tables</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>cache_timeout</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">integer</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">3600</div>
                </td>
                    <td>
                            <div> ini entries:
                                    <p>[defaults]<br>fact_caching_timeout = 3600</p>
                                    <p>[inventory]<br>cache_timeout = 3600</p>
                            </div>
                                <div>env:ANSIBLE_CACHE_PLUGIN_TIMEOUT</div>
                                <div>env:ANSIBLE_INVENTORY_CACHE_TIMEOUT</div>
                    </td>
                <td>
                        <div>Cache duration in seconds</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>compose</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">dictionary</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">{}</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>Create vars from jinja2 expressions.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>filters</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">list</span>
                         / <span style="color: purple">elements=string</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">[]</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>This option allows client-side filtering hosts with jinja templating.</div>
                        <div>When server-side filtering is introduced, it should be preferred over this.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>groups</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">dictionary</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">{}</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>Add hosts to group based on Jinja2 conditionals.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>hostname</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">-</span>
                         / <span style="color: red">required</span>
                    </div>
                </td>
                <td>
                </td>
                    <td>
                                <div>env:VMWARE_HOST</div>
                                <div>env:VMWARE_SERVER</div>
                    </td>
                <td>
                        <div>Name of vCenter or ESXi server.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>hostnames</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">list</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">["config.name + \"_\" + config.uuid"]</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>A list of templates in order of precedence to compose inventory_hostname.</div>
                        <div>Ignores template if resulted in an empty string or None value.</div>
                        <div>You can use property specified in <em>properties</em> as variables in the template.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>keyed_groups</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">list</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">[{"key": "config.guestId", "separator": ""}, {"key": "summary.runtime.powerState", "separator": ""}]</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>Add hosts to group based on the values of a variable.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>password</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">-</span>
                         / <span style="color: red">required</span>
                    </div>
                </td>
                <td>
                </td>
                    <td>
                                <div>env:VMWARE_PASSWORD</div>
                    </td>
                <td>
                        <div>Password of vSphere user.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>port</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">-</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">443</div>
                </td>
                    <td>
                                <div>env:VMWARE_PORT</div>
                    </td>
                <td>
                        <div>Port number used to connect to vCenter or ESXi Server.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>properties</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">list</span>
                    </div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">["name", "config.cpuHotAddEnabled", "config.cpuHotRemoveEnabled", "config.instanceUuid", "config.hardware.numCPU", "config.template", "config.name", "config.uuid", "guest.hostName", "guest.ipAddress", "guest.guestId", "guest.guestState", "runtime.maxMemoryUsage", "customValue", "summary.runtime.powerState", "config.guestId"]</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>Specify the list of VMware schema properties associated with the VM.</div>
                        <div>These properties will be populated in hostvars of the given VM.</div>
                        <div>Each value in the list can be a path to a specific property in VM object or a path to a collection of VM objects.</div>
                        <div><code>config.name</code>, <code>config.uuid</code> are required properties if <code>hostnames</code> is set to default.</div>
                        <div><code>config.guestId</code>, <code>summary.runtime.powerState</code> are required if <code>keyed_groups</code> is set to default.</div>
                        <div>Please make sure that all the properties that are used in other parameters are included in this options.</div>
                        <div>In addition to VM properties, the following are special values</div>
                        <div>Use <code>customValue</code> to populate virtual machine&#x27;s custom attributes. <code>customValue</code> is only supported by vCenter and not by ESXi.</div>
                        <div>Use <code>all</code> to populate all the properties of the virtual machine. The value <code>all</code> is time consuming operation, do not use unless required absolutely.</div>
                        <div>Please refer more VMware guest attributes which can be used as properties <a href='https://github.com/ansible/ansible/blob/devel/docs/docsite/rst/scenario_guides/vmware_scenarios/vmware_inventory_vm_attributes.rst'>https://github.com/ansible/ansible/blob/devel/docs/docsite/rst/scenario_guides/vmware_scenarios/vmware_inventory_vm_attributes.rst</a></div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>resources</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">list</span>
                    </div>
                    <div style="font-style: italic; font-size: small; color: darkgreen">added in 2.10</div>
                </td>
                <td>
                        <b>Default:</b><br/><div style="color: blue">[]</div>
                </td>
                    <td>
                    </td>
                <td>
                        <div>A list of resources to limit search scope.</div>
                        <div>Each resource item is represented by exactly one <code>&#x27;vim_type_snake_case</code>:<code>list of resource names</code> pair and optional nested <em>resources</em></div>
                        <div>Key name is based on snake case of a vim type name; e.g <code>host_system</code> correspond to <code>vim.HostSystem</code></div>
                        <div>See  <a href='https://pubs.vmware.com/vi-sdk/visdk250/ReferenceGuide/index-mo_types.html'>VIM Types</a></div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>strict</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                    <td>
                    </td>
                <td>
                        <div>If <code>yes</code> make invalid entries a fatal error, otherwise skip and continue.</div>
                        <div>Since it is possible to use facts in the expressions they might not always be available and we ignore those errors by default.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>username</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">-</span>
                         / <span style="color: red">required</span>
                    </div>
                </td>
                <td>
                </td>
                    <td>
                                <div>env:VMWARE_USER</div>
                                <div>env:VMWARE_USERNAME</div>
                    </td>
                <td>
                        <div>Name of vSphere user.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>validate_certs</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li>no</li>
                                    <li><div style="color: blue"><b>yes</b>&nbsp;&larr;</div></li>
                        </ul>
                </td>
                    <td>
                                <div>env:VMWARE_VALIDATE_CERTS</div>
                    </td>
                <td>
                        <div>Allows connection when SSL certificates are not valid.</div>
                        <div>Set to <code>false</code> when certificates are not trusted.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>with_nested_properties</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                    <td>
                    </td>
                <td>
                        <div>This option transform flatten properties name to nested dictionary.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>with_path</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                    <td>
                    </td>
                <td>
                        <div>Include virtual machines path.</div>
                        <div>Set this option to a string value to replace root name from <em>&#x27;Datacenters&#x27;</em>.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>with_sanitized_property_name</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                    <td>
                    </td>
                <td>
                        <div>This option allows property name sanitization to create safe property names for use in Ansible.</div>
                        <div>Also, transforms property name to snake case.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>with_tags</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                    <td>
                    </td>
                <td>
                        <div>Include tags and associated virtual machines.</div>
                        <div>Requires &#x27;vSphere Automation SDK&#x27; library to be installed on the given controller machine.</div>
                        <div>Please refer following URLs for installation steps</div>
                        <div><a href='https://code.vmware.com/web/sdk/7.0/vsphere-automation-python'>https://code.vmware.com/web/sdk/7.0/vsphere-automation-python</a></div>
                </td>
            </tr>
    </table>
    <br/>




Examples
--------

.. code-block:: yaml+jinja

    # Sample configuration file for VMware Guest dynamic inventory
        plugin: community.vmware.vmware_vm_inventory
        strict: False
        hostname: 10.65.223.31
        username: administrator@vsphere.local
        password: Esxi@123$%
        validate_certs: False
        with_tags: True

    # Gather minimum set of properties for VMware guest
        plugin: community.vmware.vmware_vm_inventory
        strict: False
        hostname: 10.65.223.31
        username: administrator@vsphere.local
        password: Esxi@123$%
        validate_certs: False
        properties:
        - 'name'
        - 'guest.ipAddress'

    # Create Groups based upon VMware Tools status
        plugin: community.vmware.vmware_vm_inventory
        strict: False
        hostname: 10.65.223.31
        username: administrator@vsphere.local
        password: Esxi@123$%
        validate_certs: False
        with_tags: False
        properties:
        - 'name'
        - 'config.name'
        - 'guest.toolsStatus'
        - 'guest.toolsRunningStatus'
        hostnames:
        - config.name
        keyed_groups:
        - key: guest.toolsStatus
          separator: ''
        - key: guest.toolsRunningStatus
          separator: ''

    # Filter VMs based upon condition
        plugin: community.vmware.vmware_vm_inventory
        strict: False
        hostname: 10.65.223.31
        username: administrator@vsphere.local
        password: Esxi@123$%
        validate_certs: False
        properties:
        - runtime.powerState
        - config.name
        filters:
        - runtime.powerState == "poweredOn"
        hostnames:
        - config.name

    # Using compose and groups
        plugin: community.vmware.vmware_vm_inventory
        strict: False
        hostname: 10.65.223.31
        username: administrator@vsphere.local
        password: Esxi@123$%
        validate_certs: False
        with_tags: False
        properties:
        - 'name'
        - 'config.name'
        - 'guest.ipAddress'
        compose:
          # This will populate the IP address of virtual machine if available
          # and will be used while communicating to the given virtual machine
          ansible_host: 'guest.ipAddress'
          composed_var: 'config.name'
        groups:
          VMs: True
        hostnames:
        - config.name

    # Use Datacenter, Cluster and Folder value to list VMs
        plugin: community.vmware.vmware_vm_inventory
        strict: False
        hostname: 10.65.200.241
        username: administrator@vsphere.local
        password: Esxi@123$%
        validate_certs: False
        with_tags: True
        resources:
          - datacenter:
            - Asia-Datacenter1
            - Asia-Datacenter2
            resources:
            - compute_resource:
              - Asia-Cluster1
              resources:
              - host_system:
                - Asia-ESXI4
            - folder:
              - dev
              - prod




Status
------


Authors
~~~~~~~

- Abhijeet Kasurde (@Akasurde)


.. hint::
    Configuration entries for each entry type have a low to high priority order. For example, a variable that is lower in the list will override a variable that is higher up.
