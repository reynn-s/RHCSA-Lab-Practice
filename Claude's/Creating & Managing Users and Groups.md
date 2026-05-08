I asked claude to make me a lab for Creating & Managing Users and Groups. Claude made me two lab.

## 1st Lab:
- Create users alice and bob with home directories
- Create a group called webteam with GID 1050
- Add both users to webteam
- Verify Group membership with id

Solution for the 1st Lab:
```
useradd -m alice
useradd -m bob
```
``` -m ``` option explanation: its a short version for ``` --create-home ```. it creates the user's home directory

```
groupadd -g 1050 webteam
```

```-g ``` option explanation: its a short version for ```--gid```. it specifies the group id

```
usermod -aG webteam alice
usermod -aG webteam bob
```

```-aG``` option explanation: this option append a user to another supplementary group it doesnt remove the user previous group. it adds the user to another group.

```
id alice
```

## 2nd Lab:
- set alice's password to RedHat123!
- force alice to change password on next login
- set max password age to 90 days, min 7 days, warn at 14 days
- lock bob's account, then unlock it
- verify aging settings with chage -l alice

Solution for 2nd Lab:

``` 
passwd alice
```

and then input the RedHat123! password

``` 
chage -d 0 alice
```

``` -d ``` option explanation: this is the short form for ``` --lastday ``` set dates of last password to change. in the example i give 0 so the next first login forcing alice to change the password.

``` 
chage -M 90 -m 7 -W 14 alice
```

``` -M ``` option explanation: this is the short form for ``` --maxdays ```. it sets the age maximum password.

``` -m ``` option explanation: this is the short form for ``` --mindays ```. it makes a delay before alice change the password again.

``` -W ``` option explanation: this is the short form for ``` --warndays ```. expiration warning days.


``` 
passwd -l bob
``` 

``` -l ``` option explanation: this is the short form for ``` --lock ```. this locks the password for the user.


``` 
passwd -u bob
```

``` -u ``` option explanation: this is the short form for ``` --unlock ```. this unlocks the password for the user.
