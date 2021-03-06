# Pipelines API

## List project pipelines

> [Introduced][ce-5837] in GitLab 8.11

```
GET /projects/:id/pipelines
```

| Attribute | Type    | Required | Description         |
|-----------|---------|----------|---------------------|
| `id`      | integer | yes      | The ID of a project |

```
curl --header "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" "https://gitlab.example.com/api/v3/projects/1/pipelines"
```

Example of response

```json
[
  {
    "id": 47,
    "status": "pending",
    "ref": "new-pipeline",
    "sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
    "before_sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
    "tag": false,
    "yaml_errors": null,
    "user": {
      "name": "Administrator",
      "username": "root",
      "id": 1,
      "state": "active",
      "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
      "web_url": "http://localhost:3000/root"
    },
    "created_at": "2016-08-16T10:23:19.007Z",
    "updated_at": "2016-08-16T10:23:19.216Z",
    "started_at": null,
    "finished_at": null,
    "committed_at": null,
    "duration": null,
    "coverage": "30.0"
  },
  {
    "id": 48,
    "status": "pending",
    "ref": "new-pipeline",
    "sha": "eb94b618fb5865b26e80fdd8ae531b7a63ad851a",
    "before_sha": "eb94b618fb5865b26e80fdd8ae531b7a63ad851a",
    "tag": false,
    "yaml_errors": null,
    "user": {
      "name": "Administrator",
      "username": "root",
      "id": 1,
      "state": "active",
      "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
      "web_url": "http://localhost:3000/root"
    },
    "created_at": "2016-08-16T10:23:21.184Z",
    "updated_at": "2016-08-16T10:23:21.314Z",
    "started_at": null,
    "finished_at": null,
    "committed_at": null,
    "duration": null,
    "coverage": null
  }
]
```

## Get a single pipeline

> [Introduced][ce-5837] in GitLab 8.11

```
GET /projects/:id/pipelines/:pipeline_id
```

| Attribute  | Type    | Required | Description         |
|------------|---------|----------|---------------------|
| `id`       | integer | yes      | The ID of a project |
| `pipeline_id` | integer | yes      | The ID of a pipeline   |

```
curl --header "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" "https://gitlab.example.com/api/v3/projects/1/pipeline/46"
```

Example of response

```json
{
  "id": 46,
  "status": "success",
  "ref": "master",
  "sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
  "before_sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
  "tag": false,
  "yaml_errors": null,
  "user": {
    "name": "Administrator",
    "username": "root",
    "id": 1,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
    "web_url": "http://localhost:3000/root"
  },
  "created_at": "2016-08-11T11:28:34.085Z",
  "updated_at": "2016-08-11T11:32:35.169Z",
  "started_at": null,
  "finished_at": "2016-08-11T11:32:35.145Z",
  "committed_at": null,
  "duration": null,
  "coverage": "30.0"
}
```

## Create a new pipeline

> [Introduced][ce-7209] in GitLab 8.14

```
POST /projects/:id/pipeline
```

| Attribute  | Type    | Required | Description         |
|------------|---------|----------|---------------------|
| `id`       | integer | yes      | The ID of a project |
| `ref`       | string | yes      | Reference to commit |

```
curl --request POST --header "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" "https://gitlab.example.com/api/v3/projects/1/pipeline?ref=master"
```

Example of response

```json
{
  "id": 61,
  "sha": "384c444e840a515b23f21915ee5766b87068a70d",
  "ref": "master",
  "status": "pending",
  "before_sha": "0000000000000000000000000000000000000000",
  "tag": false,
  "yaml_errors": null,
  "user": {
    "name": "Administrator",
    "username": "root",
    "id": 1,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
    "web_url": "http://localhost:3000/root"
  },
  "created_at": "2016-11-04T09:36:13.747Z",
  "updated_at": "2016-11-04T09:36:13.977Z",
  "started_at": null,
  "finished_at": null,
  "committed_at": null,
  "duration": null,
  "coverage": null
}
```

## Retry failed builds in a pipeline

> [Introduced][ce-5837] in GitLab 8.11

```
POST /projects/:id/pipelines/:pipeline_id/retry
```

| Attribute  | Type    | Required | Description         |
|------------|---------|----------|---------------------|
| `id`       | integer | yes      | The ID of a project |
| `pipeline_id` | integer | yes   | The ID of a pipeline |

```
curl --header "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" "https://gitlab.example.com/api/v3/projects/1/pipelines/46/retry"
```

Response:

```json
{
  "id": 46,
  "status": "pending",
  "ref": "master",
  "sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
  "before_sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
  "tag": false,
  "yaml_errors": null,
  "user": {
    "name": "Administrator",
    "username": "root",
    "id": 1,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
    "web_url": "http://localhost:3000/root"
  },
  "created_at": "2016-08-11T11:28:34.085Z",
  "updated_at": "2016-08-11T11:32:35.169Z",
  "started_at": null,
  "finished_at": "2016-08-11T11:32:35.145Z",
  "committed_at": null,
  "duration": null,
  "coverage": null
}
```

## Cancel a pipelines builds

> [Introduced][ce-5837] in GitLab 8.11

```
POST /projects/:id/pipelines/:pipeline_id/cancel
```

| Attribute  | Type    | Required | Description         |
|------------|---------|----------|---------------------|
| `id`       | integer | yes      | The ID of a project |
| `pipeline_id` | integer | yes   | The ID of a pipeline |

```
curl --header "PRIVATE-TOKEN: 9koXpg98eAheJpvBs5tK" "https://gitlab.example.com/api/v3/projects/1/pipelines/46/cancel"
```

Response:

```json
{
  "id": 46,
  "status": "canceled",
  "ref": "master",
  "sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
  "before_sha": "a91957a858320c0e17f3a0eca7cfacbff50ea29a",
  "tag": false,
  "yaml_errors": null,
  "user": {
    "name": "Administrator",
    "username": "root",
    "id": 1,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
    "web_url": "http://localhost:3000/root"
  },
  "created_at": "2016-08-11T11:28:34.085Z",
  "updated_at": "2016-08-11T11:32:35.169Z",
  "started_at": null,
  "finished_at": "2016-08-11T11:32:35.145Z",
  "committed_at": null,
  "duration": null,
  "coverage": null
}
```

[ce-5837]: https://gitlab.com/gitlab-org/gitlab-ce/merge_requests/5837
[ce-7209]: https://gitlab.com/gitlab-org/gitlab-ce/merge_requests/7209
