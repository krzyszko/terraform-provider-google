---
layout: "google"
page_title: "Google: google_organization_iam_binding"
sidebar_current: "docs-google-organization-iam-binding"
description: |-
 Allows management of a single binding with an IAM policy for a Google Cloud Platform Organization.
---

# google\_organization\_iam\_binding

Allows creation and management of a single binding within IAM policy for
an existing Google Cloud Platform Organization.

~> **Note:** This resource __must not__ be used in conjunction with
   `google_organization_iam_member` for the __same role__ or they will fight over
   what your policy should be.

## Example Usage

```hcl
resource "google_organization_iam_binding" "binding" {
  org_id = "123456789"
  role    = "roles/browser"

  members = [
    "user:jane@example.com",
  ]
}
```

## Argument Reference

The following arguments are supported:

* `org_id` - (Required) The numeric ID of the organization in which you want to create a custom role.

* `role` - (Required) The role that should be applied. Only one
    `google_organization_iam_binding` can be used per role.

* `members` - (Required) A list of users that the role should apply to.

## Attributes Reference

In addition to the arguments listed above, the following computed attributes are
exported:

* `etag` - (Computed) The etag of the organization's IAM policy.

