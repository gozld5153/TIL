# AWS CLI Error "You must specify a region. You can also configure your region by running 'aws configure'". 

1. CLI에 profile option을 줬다며 해당 profile 설정에 region이 설정되어 있는지 확인한다.
```bash
aws configure list --profile {profileName}
```

2. 해당 profile에 region 설정이 되어 있지 않다면 region 설정
```bash
aws configure set region {regionName} --profile {profileName}
```
