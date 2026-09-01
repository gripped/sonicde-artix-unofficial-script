Repo at https://github.com/gripped/sonicde-artix-unofficial

All options are set within the script near the top.

    # Options
    ccache = False
    ccache_dir = '/media/Spare_SSD/ccache'
    cleanup = False
    cwd = '' # Set this to an existing dir or your cwd will be used. I.e. the dir you run the script from.
    key_dir = '/root/sonicde-key'
    key_fp = '8F74E8CCCB380B1D598B13C8FFA739AC998BD51A'
    key_private_name = 'sonicde-artix-unofficial-private.asc'
    key_public_name = 'sonicde-artix-unofficial-public.asc'
    print_sys_cmds = True
    quiet = False
    safe_efi = True
    save_last_commit = False
    sign_packages = False
    packager = 'bob not@here.com'
    user = ''
    # End options

**ccache & ccache_dir**
If ccache = True bind mount ccache_dir to the chroot and use ccache

**cleanup**
If True delete the chroot at the end

**cwd** 
Directory where the chroot is created and the resulting packages and PKGBUILD's are left at the end. If you don't set it it will use the current working dir. So you probably should set it. Must exist if set.

**key_dir key_fp key_private_name key_public_name sign_packages**
If sign_packages =True set the rest with the location names and fingerprint of your keys.

**print_sys_cmds**
If true system commands (subprocess.Popen) used will be output.

**quiet**
Suppress much output.

**safe_efi**
If True will remount /sys/firmware/efi/efivars read only then back to rw at the end.
Not all the efivars are immutable. And as it gets mounted when the needed /sys is mounted it's safer imo. 

**save_last_commit**
If True the last commit is saved to /var/tmp/sonicde-artix-unofficial/commit and on the next run the script will stop if there are no new commits.

**packager**
added to the temporary makepkg.conf

**user**
The user name to run the part of the script that don't run as root. If unset uid 1000 is used.

Git must be installed.
