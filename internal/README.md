# `/internal`

Private application and library code. This is the code you don't want others importing in their applications or libraries. Note that this layout pattern is enforced by the Go compiler itself. See the Go 1.4 [`release notes`](https://golang.org/doc/go1.4#internalpackages) for more details. Note that you are not limited to the top level `internal` directory. You can have more than one `internal` directory at any level of your project tree.

You can optionally add a bit of extra structure to your internal packages to separate your shared and non-shared internal code. It's not required (especially for smaller projects), but it's nice to have visual clues showing the intended package use. Your actual application code can go in the `/internal/app` directory (e.g., `/internal/app/myapp`) and the code shared by those apps in the `/internal/pkg` directory (e.g., `/internal/pkg/myprivlib`).

Examples:

* https://github.com/hashicorp/terraform/tree/master/internal
* https://github.com/influxdata/influxdb/tree/master/internal
* https://github.com/perkeep/perkeep/tree/master/internal
* https://github.com/jaegertracing/jaeger/tree/master/internal
* https://github.com/moby/moby/tree/master/internal
* https://github.com/satellity/satellity/tree/master/internal

## `/internal/pkg`

`/internal` 层共享库存放位置

Examples:

* https://github.com/hashicorp/waypoint/tree/main/internal/pkg

## `/internal/service`

api 定义的实现层，只做 DTO->DO 的转换，组装biz层的逻辑。不要带业务逻辑。

## `/internal/biz`

业务逻辑的组装层，repo （Repository） 接口在这里定义，使用依赖倒置原则。

## `internal/data`

业务数据访问，包含 cache、db 等封装，实现了 biz 的 repo 接口