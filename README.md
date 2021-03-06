# polkasign-backend

## build graphql
```bash
go run github.com/99designs/gqlgen generate
```

## start server
```bash
go build -o server ./server.go 
nohup ./server &
```

## install npm modules
```bash
cd subscriber
nvm install 14.16.0
nvm use 14.16.0
npm install -g yarn
yarn
```

## start subscriber
```bash
cd subscriber
nohup node subscribe.js &
```

## query agreementInfos
### agreementInfos query
```json
query {
	agreementInfos(filter: {
    creator: "5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY",
    signer: "5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY",
    status: [0]
  },
  page: {
    page: 0,
    size: 2,
    sortField: "index",
    order: "desc"
  }){
    page,
    size,
    total,
    data {
      index,
      creator,
      name,
      create_at,
      status,
      signers,
      agreement_file,
      sign_infos,
      resources
    }
}
}
```

result
```json
{
  "data": {
    "agreementInfos": {
      "page": 0,
      "size": 2,
      "total": 2,
      "data": [
        {
          "index": 12,
          "creator": "5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY",
          "name": "wqwqwqwq",
          "create_at": "1,637,427,330,003",
          "status": 0,
          "signers": ",5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY,",
          "agreement_file": "{\"hash_\":\"0x6f88ed5ee10a1a67343c6082d2f9d322cd3d1eacc4a4657c341cc7b56bcd6173\",\"creator\":\"5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY\",\"usage\":\"2\",\"saveAt\":\"2\",\"url\":\"2\"}",
          "sign_infos": "[]",
          "resources": "[{\"hash_\":\"0x6f88ed5ee10a1a67343c6082d2f9d322cd3d1eacc4a4657c341cc7b56bcd6173\",\"creator\":\"5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY\",\"usage\":\"2\",\"saveAt\":\"3\",\"url\":\"2\"}]"
        },
        {
          "index": 7,
          "creator": "5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY",
          "name": "test33",
          "create_at": "1,637,426,292,002",
          "status": 0,
          "signers": ",5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY,",
          "agreement_file": "{\"hash_\":\"0x6f88ed5ee10a1a67343c6082d2f9d322cd3d1eacc4a4657c341cc7b56bcd6173\",\"creator\":\"5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY\",\"usage\":\"1\",\"saveAt\":\"1\",\"url\":\"1\"}",
          "sign_infos": "[]",
          "resources": "[]"
        }
      ]
    }
  }
}
```

### createAgreementInfo

```json
mutation {
  createAgreementInfo(input: {
    index: 2000,
    creator: "23333",
    name: "123",
    create_at: "1",
    status: 1,
    signers: ",123,",
    agreement_file: "123",
    sign_infos: "123",
    resources: "123"
  }){
    index,
    creator,
    name,
    create_at,
    status,
    signers,
    agreement_file,
    sign_infos,
    resources
  }
}
```