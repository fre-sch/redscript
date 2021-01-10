# redscript
Toolkit for working with scripts used by REDengine in Cyberpunk 2077.
Currently only includes a disassembler and a decompiler.

## usage
```
  -i, --input INPUT    input file
  -o, --output OUTPUT  output file or directory
  -m, --mode MODE      dump mode (one of: 'ast', 'bytecode' or 'code')
  -f, --dump-files     split into individual files (doesn't work for everything yet)
```

You can build the project and decompile all scripts in one command:
```bash
cargo run --release -- -i '/mnt/d/games/Cyberpunk 2077/r6/cache/final.redscript' -o classes.redscript
```

## output
The scripts are decompiled into a Java-like language:
```
  public Handle<GameObject> GetReprimandPerformer(EntityID target) {
    Agent agent;
    Handle<GameObject> performer;
    Handle<DeviceComponentPS> ps;
    if(!IsDefined(target)) {
      target = GetPlayer(GetGameInstance()).GetEntityID();
    };
    if(this.m_agentsRegistry.GetReprimandPerformer(target, agent)) {
      ps = GetPS(agent.link);
      return Cast(ToHandle(ps.GetOwnerEntityWeak()));
    };
    return null;
  }
```