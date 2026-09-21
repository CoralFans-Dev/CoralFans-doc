# Q&A

## Does it work on Linux?

Not directly. Currently neither LeviLamina nor CF directly supports Linux. You may need tools like `wine` to emulate a Windows environment to run it.

## Does it work in singleplayer / on mobile?

Not directly. CF is a server plugin. You can run a local server and then join it in singleplayer or from your phone.

## Does it work on Realms?

No. Realms has no plugin loader.

## I'm using some (possibly free/panel) server provider, does it work?

Not necessarily. It depends on whether they provide a BDS with LeviLamina server. Without LeviLamina this plugin cannot run. Suggestion: use a VPS to build your own server.

## What if I can't understand the tutorial?

If something in the tutorial is unclear, feel free to open an Issue/PR.

## I'm not good at Chinese

Sorry, I'm not good at English. -- odorajbotoj

I18N coming soon.

## What if my visualization doesn't show up?

Check whether the prerequisite resource pack is loaded and globally enabled.

## Does it work on version 1.xx.xx?

CF is currently based on LL 26.51.x, with BDS version 1.26.51. Starting from 26.51, CoralFans and LeviLamina version numbers are aligned with the BDS minor version number. Please refer to the corresponding version on the plugin release page.

## Does it work on the client (not a server)?

Yes. Since 26.10, CF has been adapted to the client version of LeviLamina and can be installed as a client mod (placed in the `mods/` directory), in which case features such as keyboard shortcuts are available.

## Will it be adapted to new versions?

Depends on whether the loader can be updated.

## What if the simulated player keeps crashing?

Note that the simulated player system bundled with old versions of CF is incompatible with CFSP and contains many bugs. Please update your CF and CFSP.

You can analyze the log files and open an issue. We will read it.
