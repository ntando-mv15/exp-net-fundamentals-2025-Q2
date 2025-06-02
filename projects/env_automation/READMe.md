## How to Deploy

### Check Your AWS Account

The following command will tell you who you are logged in as. 
This step assumes you have installed and setup AWS CLI.

```sh
aws sts get-caller-identity
```

### Run Deploy Script
```sh
cd projects/env_automation
chmod u+x ./bin/deploy
./bin/deploy
```

> you only have to chmod the file once to make it executable.

---

## Troubleshooting
### ⚠️ WSL Users: 

If you're using **Windows Subsystem for Linux (WSL)** and encounter this error when running scripts:

```bash
/usr/bin/env: ‘bash\r’: No such file or directory
```

#### Fix the script by converting line endings:

Using `dos2unix`:

```bash
sudo apt install dos2unix  # only needed once
dos2unix ./bin/deploy
```

Then re-run:

```bash
chmod +x ./bin/deploy
./bin/deploy
```

---
