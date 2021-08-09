# BitBurnerScripts
A collection of my bitburner scripts for backup/sharing purposes.

# Installation
1. Create a new script called start.ns by issuing the following command: nano start.ns. Make sure you're on your home server if you're not (you can quickly go home by running home in the console).
2. Paste the following content:
```javascript
export async function main(ns) {
  if (ns.getHostname() !== "home") {
    throw new Exception("Run the script from home");
  }

  await ns.wget(
    `https://raw.githubusercontent.com/JoshNotWright/BitBurnerScripts/master/initDaemon.ns?ts=${new Date().getTime()}`,
    "initDaemon.ns"
  );
  ns.spawn("initDaemon.ns", 1);
}
```
3. Exit the nano and write in console: `run start.ns`
