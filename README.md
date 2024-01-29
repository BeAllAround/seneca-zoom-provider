![Seneca Tangocard-Provider](http://senecajs.org/files/assets/seneca-logo.png)

> _Seneca Zoom-Provider_ is a plugin for [Seneca](http://senecajs.org)


Provides access to the Zoom API using the Seneca *provider*
convention. Zoom API entities are represented as Seneca entities so
that they can be accessed using the Seneca entity API and messages.

See [seneca-entity](senecajs/seneca-entity) and the [Seneca Data
Entities
Tutorial](https://senecajs.org/docs/tutorials/understanding-data-entities.html) for more details on the Seneca entity API.

NOTE: underlying third party SDK needs to be replaced as out of date and has a security issue.

[![npm version](https://img.shields.io/npm/v/@seneca/tangocard-provider.svg)](https://npmjs.com/package/@seneca/tangocard-provider)
[![build](https://github.com/senecajs/seneca-tangocard-provider/actions/workflows/build.yml/badge.svg)](https://github.com/senecajs/seneca-tangocard-provider/actions/workflows/build.yml)
[![Coverage Status](https://coveralls.io/repos/github/senecajs/seneca-tangocard-provider/badge.svg?branch=main)](https://coveralls.io/github/senecajs/seneca-tangocard-provider?branch=main)
[![Known Vulnerabilities](https://snyk.io/test/github/senecajs/seneca-tangocard-provider/badge.svg)](https://snyk.io/test/github/senecajs/seneca-tangocard-provider)
[![DeepScan grade](https://deepscan.io/api/teams/5016/projects/19462/branches/505954/badge/grade.svg)](https://deepscan.io/dashboard#view=project&tid=5016&pid=19462&bid=505954)
[![Maintainability](https://api.codeclimate.com/v1/badges/f76e83896b731bb5d609/maintainability)](https://codeclimate.com/github/senecajs/seneca-tangocard-provider/maintainability)


| ![Voxgig](https://www.voxgig.com/res/img/vgt01r.png) | This open source module is sponsored and supported by [Voxgig](https://www.voxgig.com). |
|---|---|


## Quick Example


```js

// Setup - get the key value (<SECRET>) separately from a vault or
// environment variable.
Seneca()
  // Get API keys using the seneca-env plugin
  .use('env', {
    var: {
      $ZOOM_CLIENT_SECRET: String,
      $ZOOM_ACCOUNT_ID: String,
      $ZOOM_CLIENT_ID: String,
    }
  })
  .use('provider', {
    provider: {
      zoom: {
        keys: {
          client_secret: { value: '$ZOOM_CLIENT_SECRET' },
          account_id: { value: '$ZOOM_ACCOUNT_ID' },
          client_id: { value: '$ZOOM_CLIENT_ID' }
        }
      }
    }
  })
  .use('zoom-provider')

let meeting = await seneca.entity('provider/zoom/meeting')
  .load$('<zoom-meeting-id>')

Console.log('MEETING', meeting)

meeting.start_time = new Date()
meeting = await meeting.save$()

Console.log('UPDATED MEETING', meeting)

```

## Install

```sh
$ npm install @seneca/zoom-provider @seneca/env
```



<!--START:options-->


## Options

* `debug` : boolean <i><small>false</small></i>


Set plugin options when loading with:
```js


seneca.use('ZoomProvider', { name: value, ... })


```


<small>Note: <code>foo.bar</code> in the list above means 
<code>{ foo: { bar: ... } }</code></small> 



<!--END:options-->

<!--START:action-list-->


## Action Patterns

* [role:entity,base:zoom,cmd:load,name:repo,zone:provider](#-roleentitybasezoomcmdloadnamerepozoneprovider-)
* [role:entity,base:zoom,cmd:save,name:repo,zone:provider](#-roleentitybasezoomcmdsavenamerepozoneprovider-)
* [sys:provider,get:info,provider:zoom](#-sysprovidergetinfoproviderzoom-)


<!--END:action-list-->

<!--START:action-desc-->


## Action Descriptions

### &laquo; `role:entity,base:zoom,cmd:load,name:repo,zone:provider` &raquo;

Load Zoom repository data into an entity.



----------
### &laquo; `role:entity,base:zoom,cmd:save,name:repo,zone:provider` &raquo;

Update Zoom repository data from an entity.



----------
### &laquo; `sys:provider,get:info,provider:zoom` &raquo;

Get information about the provider.



----------


<!--END:action-desc-->
