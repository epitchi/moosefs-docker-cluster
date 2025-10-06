#### Mount user_data and app_data
`shell
mfsmount -H [HOST_IP] -S [SUB_FOLDER_PATH](Inside master chunk) [PATH_MOUNTPOINT]
`

```shell
sudo mfsmount -H 10.30.30.0 -S /app_data /app_data

sudo mfsmount -H 10.30.30.0 -S /user_data /user_data
```

#### Unmount 
`sudo umount -l [mountpoint]`
```shell
sudo umount -l /user_data
```

#### Create snapshot
**mfs command only work on mfs tree**
    
    mount all dir of mfsmaster into /mnt/moosefs/ to easy work with mfs command

`sudo mfsmakesnapshot [SOURCE_FILE] [DESTINATION_FILE]`
```shell
huyhoang@mfsmaster:$ sudo mfsmakesnapshot /mnt/moosefs/app_data/abc.qcow2 /mnt/moosefs/user_data/abc.qcow2
```

### Trash Handle
|root   |
        |trash
        |sustained
**your trash locate at /trash, after delete in trash, it move to sustained to handle delete on all chunk server. so it wil take little to reblance space**
```shell
huyhoang@mfsmaster:$ sudo mfsmount -H 10.30.30.0 -o mfsmeta,mfsflattrash /mnt/trash/
```

#### Update (Append) snapshot
//todo