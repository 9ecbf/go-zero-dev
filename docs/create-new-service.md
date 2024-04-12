# Create new service

New service can be created by running the following command:

```sh
bun new <service>
```

where `<service>` is name of the service to be created.

If the creation is successful, the source code will be located at the `services/<service>` directory with a structure like:

```txt
./services
├── <service>
│   ├── etc
│   │   └── <service>-api.yaml // configuration file
│   ├── internal
│   │   ├── config
│   │   │   └── config.go // configuration definition
│   │   ├── handler
│   │   │   ├── <service>handler.go // default handler
│   │   │   └── routes.go // routes definition
│   │   ├── logic
│   │   │   └── <service>logic.go // business logic
│   │   ├── svc
│   │   │   └── servicecontext.go // defines ServiceContext
│   │   └── types
│   │       └── types.go // defines request/response
│   ├── <service>.api
│   └── <service>.go // main entrance
├── go.mod
└── go.sum
```
