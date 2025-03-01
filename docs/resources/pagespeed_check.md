---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "statuscake_pagespeed_check Resource - terraform-provider-statuscake"
subcategory: ""
description: |-
  
---

# statuscake_pagespeed_check (Resource)



## Example Usage

```terraform
resource "statuscake_pagespeed_check" "example_com" {
  name           = "Example"
  check_interval = 300
  region         = "UK"

  contact_groups = [
    statuscake_contact_group.operations_team.id
  ]

  alert_config {
    alert_bigger = "5000"
  }

  monitored_resource {
    address = "https://www.example.com"
  }
}

output "example_com_pagespeed_check_id" {
  value = statuscake_pagespeed_check.example_com.id
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **alert_config** (Block List, Min: 1, Max: 1) Alert configuration block. Omitting this block disabled all alerts (see [below for nested schema](#nestedblock--alert_config))
- **check_interval** (Number) Number of seconds between checks
- **monitored_resource** (Block List, Min: 1, Max: 1) Monitored resource configuration block. The describes server under test (see [below for nested schema](#nestedblock--monitored_resource))
- **name** (String) Name of the check
- **region** (String) Region on which to run checks

### Optional

- **contact_groups** (Set of String) List of contact group IDs
- **id** (String) The ID of this resource.
- **paused** (Boolean) Whether the check should be run

### Read-Only

- **location** (String) Assigned monitoring location on which checks will be run

<a id="nestedblock--alert_config"></a>
### Nested Schema for `alert_config`

Optional:

- **alert_bigger** (Number) An alert will be sent if the size of the page is larger than this value (kb).
- **alert_slower** (Number) An alert will be sent if the load time of the page exceeds this value (ms).
- **alert_smaller** (Number) An alert will be sent if the size of the page is smaller than this value (kb).


<a id="nestedblock--monitored_resource"></a>
### Nested Schema for `monitored_resource`

Required:

- **address** (String) URL or IP address of the website under test


