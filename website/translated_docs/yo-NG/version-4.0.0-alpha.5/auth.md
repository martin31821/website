---
id: version-4.0.0-alpha.5-authentification
title: Sise ijerisi
original_id: sise ijerisi
---

The authentification is tied to the auth [plugin](plugins.md) you are using. The package restrictions also is handled by the [Package Access](packages.md).

The client authentification is handled by `npm` client itself. Once you login to the application:

```bash
npm aropoolumulo --iforukosile http://localhost:4873
```

A wa tokini kan ninu `npm` iseto apo ti a seda ni apo ile olumulo. Fun alaye lekunrere nisoa `.npmrc` ka [ iwe ijoba ](https://docs.npmjs.com/files/npmrc)l.

```bash
cat .npmrc
registry=http://localhost:5555/
//localhost:5555/:_authToken="secretVerdaccioToken"
//registry.npmjs.org/:_authToken=secretNpmjsToken
```

#### Igbajade alailoruko

`verdaccio`nfayegba fun enikeni lati se igbejade alailoruko, lati se eleyi wa nilo lati se agbekale pipe ti[awon apo igbaniwole](packages.md).

Bi apeere:

```yaml
  'ile-ise mi-*':
     igbaniwole: $anonymous
    igbejade: $anonymous
    asoju: npmjs
```

As is described [on issue #212](https://github.com/verdaccio/verdaccio/issues/212#issuecomment-308578500) until `npm@5.3.0` and all minor releases **won't allow you publish without a token**.

## Imo oye awon Akojo

### Itunmo ti `$all` ati `$anonymous`

Bu a se mo *Verdaccio* nlo awon `htpasswd` ni aiyipada. Plugini na ko gbe se awon ona no `fayefun_igbawole`,`fayegba_igbejade` ati `fayegba_ako ti gbejade`. Ni eleyi, *Verdaccio* yio kapa re ni awon ona yi:

* Ti o ba ti se agbawole (ako da o mo), `$all` ati `<code>$anonymous` tunmo si ikan kanna.
* If you are logged in, `$anonymous` won't be part of your groups and `$all` will match any logged user. A new group `$authenticated` will be added to the list.

Bi amu rele, `$all` ** yio jomo gbogbo awon olumulo, leyokokan yalanwon se agbewole tabi won ko se**.

** ise tele je fun ijerisi aiyipada plugini**. Ti o ban lo plugini eleyi ti o ba ini e mu ti plugini na wan gbese awon `fayegba_igbaniwole`, `fayegba_igbajade` tabi `fayegba_aitigbejade`, ibi ti a paju de si fun igbaniwole da lori plugini na gangan. Verdaccio akan seto awon akojo alaiyipada nikan.

Ejeki a gbeyewo gbogbo oun tati ko:

* **gbawole**: `$all`. `$authenticated` + awon akojo ti a fikun nipase plugini na
* **aidanimo (igbejade): `$all` ati `$anonymous`.</li> </ul> 
    
    ## Default htpasswd
    
    In order to simplify the setup, `verdaccio` use a plugin based on `htpasswd`. Since version v3.0.x the `verdaccio-htpasswd` plugin is used by default.
    
    ```yaml
    auth:
      htpasswd:
        file: ./htpasswd
        # Maximum amount of users allowed to register, defaults to "+inf".
        # You can set this to -1 to disable registration.
        #max_users: 1000
    ```
    
    | Property  | Type   | Required | Example    | Support | Description                              |
    | --------- | ------ | -------- | ---------- | ------- | ---------------------------------------- |
    | file      | string | Yes      | ./htpasswd | all     | file that host the encrypted credentials |
    | max_users | number | No       | 1000       | all     | set limit of users                       |
    
    In case to decide do not allow user to login, you can set `max_users: -1`.