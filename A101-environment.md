[↑ Back](./README.md)

# `A101` - Environment

## Downloading the SQL Developer

1. Visit Oracle's [website](https://www.oracle.com/tools/downloads/sqldev-downloads.html).
1. Download the *JDK included* version.
1. Extract the archive.

## Creating a connection

1. Create a new connection.
1. Give the connection any name (your decision).
1. Enter the server's properties:

   1. hostname: `codd.inf.unideb.hu`
   1. port: `1521`
   1. service name: `ora21cp.inf.unideb.hu`

1. Enter the *Username*: `u_neptun` (`neptun` denotes your unique Neptun-code, case insensitive)
1. At home you can enter your *Password* as well and check *Save Password*. In the classroom, you must skip this step.
1. Click on *Save*.
1. Close the window.

> [!TIP]
>
> At home, you can enter your *Password* as well and check the *Save Password* option.

## Resetting your password

> [!IMPORTANT]
> 
> By default, each freshman's account has an expired password that must be changed. Seniors still have their old passwords.

1. Right-click on the connection.
1. Option *Reset Password*.
1. Enter `debrecen` as *Current password*.
1. Choose your password and enter it as *New Password* and *Confirm Password*.
1. Do not forget your password.

> [!TIP]
>
> Feel free to change your password anytime by following these steps (except that *Current password* is your chosen one instead of the default value).

> [!WARNING]
>
> You must recognize your password.

## Connecting to the server

1. Double-click on the connection's name.
1. Enter your *Username* and *Password*
1. Click on the *Connect* button.

## Possible problems

### Forgotten password

You can message your instructor using the email address `toth.robert@inf.unideb.hu` in this case. We will help you as soon as possible:

**Subject**: DB password reset

**Message:**

> Dear Instructor,
> 
> I would like to reset my password as a Database Systems and Knowledge Representation student. My Neptun-code is: `_your Neptun-code_`
> 
> Best regards,
> 
> `_your full name_`

> [!WARNING]
>
> We process only password reset inquiries; other emails will not be processed.

### Locked account

After three (3) wrong password attempts, your account will be temporarily locked. Wait about 15 minutes and try to connect again. In the case of failure, follow the procedure given in the section *Forgotten Password*.

### Session limit exceeded

It seems that you have already opened multiple connections and reached the limit of concurrent connections. Wait until the server automatically closes the previous ones.


## Frequently asked questions

1. > How can I adjust the font size?

    *Tools* > *Preferences* > *Code Editor* > *Fonts*

1. > How can I restore the closed *Connections* panel?

    *View* > *Connections*
 