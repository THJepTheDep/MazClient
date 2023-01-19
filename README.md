# MazClient | [Mazanius.eu](https://mazanius.eu)

MazClient is a Batch library for injecting .dll files easily, while its impossible to get VAC Banned.

## Installation

Read about [batch](https://en.wikipedia.org/wiki/Batch_file) and what it is used for.

Source: Wikipedia

```bash
Change your .dll to [csgo.dll]
```

# Code:

[Pastebin.com](https://pastebin.com/KDntE4Ms)
```
@echo off
SETLOCAL EnableDelayedExpansion

echo Loading Colors...
ping localhost -n 2 >nul
color 0d 							

echo Loading Title ...
ping localhost -n 2 >nul
title MazClient V1.0

echo Loading Username And Password...
ping localhost -n 2 >nul
cls

echo Loading.
ping localhost -n 1 >nul
cls
echo Loading..
ping localhost -n 1 >nul
cls
echo Loading...
ping localhost -n 1 >nul
cls
echo Loading.
ping localhost -n 1 >nul
cls
echo Loading..
ping localhost -n 1 >nul
cls

GOTO main
 
:extract_user
ECHO Finding %2 in %1
ECHO Output: %3

DEL %3
FOR /f %%G IN (%1) DO (
    SET "var=%%G"
    SET "uid=!var:~0,1!"
    ECHO !uid!
	if "!uid!"=="%2" (
		ECHO %%G>>"%3"
	)
)
GOTO :EOF 

:user_parse
SET data=
FOR /f %%G IN (%1) DO (
	SET "data=!data!%%G"
)
SET user_name=
SET user_pass=
SET stage=1
SET "data=!data:~1%!"
SET "data=!data:~1%!"
:username_loop
SET "char=!data:~0,1!"
SET "data=!data:~1%!"
IF "%char%"=="," (
	GOTO password_loop
) ELSE (
	SET "user_name=!user_name!%char%"
)
GOTO username_loop
:password_loop
SET "char=!data:~0,1!"
SET "data=!data:~1%!"
IF "%char%"=="," (
	GOTO rank_loop
) ELSE (
	SET "user_pass=!user_pass!%char%"
)
GOTO password_loop
:rank_loop
GOTO :EOF

:main
SET /p inp_user="Enter your username: " %=%
SET /p inp_pass="Enter your password: " %=%
FOR /f %%G IN (users.txt) DO (
	DEL tmp.txt
	ECHO %%G>>"tmp.txt"
	CALL :user_parse tmp.txt
	IF "!user_name!" == "%inp_user%" (
		if "!user_pass!" == "%inp_pass%" (
			ECHO Logging in...
			ping localhost -n 3 >nul
			GOTO loggedin
		) else (
			GOTO accd
		)
	)
)
:accd
ECHO Access denied
GOTO end

:loggedin
ECHO You are logged in!
ping localhost -n 2 >nul
cls
ECHO loading client... 
ping localhost -n 3 >nul
ECHO =============================================================================================================
ECHO 		WARNING:  THIS IS JUST A BETA AND SOME FUNCTIONS MIGHT NOT WORK										
														
ECHO				WELCOME TO MAZCLIENT          	WEBSITE: MAZANIUS.EU
ECHO =============================================================================================================
ECHO 				TO START DOWNLOADING CHEATZ GO TO OUR WEBSITE
ECHO 				[The one you downloaded this client from]
ECHO 				[The Client will continue in 10 seconds]
	
ECHO =============================================================================================================
ping localhost -n 8 >nul
cls

start "" /wait cmd /c "echo Are you sure you want to continue? This will close all Steam apps.&echo(&pause"
echo Bypassing [=       ]
ping localhost -n 2 >nul
cls

echo Bypassing [==      ]
ping localhost -n 2 >nul
taskkill /IM Steam.exe /F
cls

echo Bypassing [===     ]
ping localhost -n 2 >nul
cls

echo Bypassing [====    ]
ping localhost -n 2 >nul
cls

echo Bypassing [=====   ]
ping localhost -n 2 >nul
cls

echo Bypassing [======  ]
ping localhost -n 2 >nul
cls

echo Bypassing [======= ]
ping localhost -n 2 >nul
cls

echo Bypassing [========] 
color 0a 
echo Done! 
ping localhost -n 5 >nul
cls

color 0d
ECHO Succesfully Bypassed 		 VAC Ban (Steam)
ECHO ==Succesfully_Closed_Steam_Clients_And_Bypassed_VAC_Ban>> 			 Steam_Vac_Ban_BYPASS_AND_CHEAT_SCRIPT_V0.0.1.dll



:choice
set /P c=Do you want to Inject MazCheatZ Client To your game? [Y/N]
if /I "%c%" EQU "Y" goto :somewhere
if /I "%c%" EQU "N" goto :somewhere_else
goto :choice


:somewhere

echo Injecting .dll Files.. 			This can take up to 30 seconds
ping localhost -n 5 >nul
start MazCheatZ_API.bat
ping localhost -n 3 >nul
Injector.exe --window-name Counter-Strike: Global Offensive - Direct3D 9 --inject C:\Users\%USERPROFILE%\Desktop\MazClient v1.1.0.1\MazClient\csgo.dll
ping localhost -n 15 >nul
goto :choice2

:somewhere_else

echo User Cancelled Injection.
ping localhost -n 5 >nul
pause
exit

:choice2

color 0a
cls
echo Succesfully Injected .dll files to CS:GO, press the "Insert" or "Home" button ingame to use the menu or cheat.
ping localhost -n 30 >nul
pause 

```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

## Use at your own risk

I made this project just for fun and i do not take any responsibilities if you get banned or something similar. Be careful when using MazClient. 

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
