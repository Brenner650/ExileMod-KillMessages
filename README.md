Kill Messages By GR8
=============

Beautiful Kill Messages Notifications with lots of options. Eye Apealing and made for bragging for good kills.

Media
--------------------------
COMING SOON

Installation
--------------------------

* Download [`KillMessages`](https://github.com/Gr8z/ExileMod-KillMessages/archive/master.zip),
* Move the `custom` folder into your Mission PBO.
* Open your `initPlayerLocal.sqf`.
* add `[] execVM "custom\KillMessages.sqf";` to the very top.
* Open your `ExileServer_object_player_event_onMpKilled.sqf` in your server PBO.
* Look for 
```
_killer setVariable ["ExileScore", _newKillerScore];
format["setAccountScore:%1:%2", _newKillerScore,getPlayerUID _killer] call ExileServer_system_database_query_fireAndForget;
_killMessage = format ["%1 was killed by %2", (name _victim), (name _killer)];
```
* Replace it with this:
```
_killer setVariable ["ExileScore", _newKillerScore];
_weapon = currentWeapon _killer;
_txt = (gettext (configFile >> 'cfgWeapons' >> _weapon >> 'displayName'));
_pic = (gettext (configFile >> 'cfgWeapons' >> _weapon >> 'picture'));
format["setAccountScore:%1:%2", _newKillerScore,getPlayerUID _killer] call ExileServer_system_database_query_fireAndForget;
_killMessage = format ["%1 was killed by %2", (name _victim), (name _killer)];

// Kill Messages By GR8				
Gr8s_kill_msg = [(name _killer), _pic, (name _victim), floor(_victim distance _killer), _txt, nil, nil];
publicVariable "Gr8s_kill_msg";
```

* OPTIONAL : You can Check `KillMessages.sqf` in your custom folder to configure the settings.