---
title: resource
type: processor
status: stable
categories: ["Utility"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/processor/resource.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


Resource is a processor type that runs a processor resource identified by its label.

```yml
# Config fields, showing default values
resource: ""
```

This processor allows you to reference the same configured processor resource in multiple places, and can also tidy up large nested configs. For example, the config:

```yaml
pipeline:
  processors:
    - mapping: |
        root.message = this
        root.meta.link_count = this.links.length()
        root.user.age = this.user.age.number()
```

Is equivalent to:

```yaml
pipeline:
  processors:
    - resource: foo_proc

processor_resources:
  - label: foo_proc
    mapping: |
      root.message = this
      root.meta.link_count = this.links.length()
      root.user.age = this.user.age.number()
```

You can find out more about resources [in this document.](/docs/configuration/resources)


