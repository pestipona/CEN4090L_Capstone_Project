## ssh to an ec2-instance:

use your `*.pem` key file assigned during **ec2-instance** creation.

```text
ssh -i /path/to/your-key.pem username@remote-server
```

e.g.

```text
scp -i .\pet-boarder-key-pair.pem ec2-user@34.204.44.67
```

## scp from localhost to remote host:

The `scp` (secure copy) **command** is used to securely copy files and directories between two locations over a network. When you need to authenticate using a .pem file (a private key file for SSH authentication) and specify the default SSH port (port 22), the syntax is as follows:

```text
scp -i /path/to/your-key.pem /path/to/local/file username@remote-server:/path/to/remote/directory
```

e.g.

```text
scp -i .\pet-boarder-key-pair.pem .\*.html ec2-user@34.204.44.67:
```

Here's a breakdown of this command:

* scp: Invokes the secure copy program.

* `-i /path/to/your-key.pem`: Specifies the private key file (*.pem) used for authentication. Replace /path/to/your-key.pem with the actual path to your .pem file.

* `/path/to/local/file`: The path to the file on your local machine that you want to copy. Replace this with the actual path to your file.

* `username@remote-server`: The username to log into the remote server and the hostname (or IP address) of the remote server. Replace username with the actual username and remote-server with the hostname or IP address of the server you're copying the file to.

* `/path/to/remote/directory`: The destination path on the remote server where the file will be copied. Replace this with the actual path where you want the file to go.

## scp from remote host to localhost:

```text
scp -i /path/to/your-key.pem username@ec2-instance-public-dns:/path/to/remote/file /path/to/local/destination
```