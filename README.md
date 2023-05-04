# ERROR
Collection of errors encountered and their solutions while working


### 1. `jupyter notebook` error after installing ROOT 6.26.10
   
   Following error was faced after trying to open jupyter notebook post ROOT 6.26.10 installation
   ```
   Traceback (most recent call last):
   File "/home/shubhamdutta/.local/bin/jupyter-notebook", line 8, in <module>
      sys.exit(main())
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/jupyter_core/application.py", line 270, in launch_instance
      return super(JupyterApp, cls).launch_instance(argv=argv, **kwargs)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/traitlets/config/application.py", line 663, in launch_instance
      app.initialize(argv)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/decorator.py", line 232, in fun
      return caller(func, *(extras + args), **kw)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/traitlets/config/application.py", line 87, in catch_config_error
      return method(app, *args, **kwargs)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/notebook/notebookapp.py", line 2077, in initialize
      super().initialize(argv)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/decorator.py", line 232, in fun
      return caller(func, *(extras + args), **kw)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/traitlets/config/application.py", line 87, in catch_config_error
      return method(app, *args, **kwargs)
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/jupyter_core/application.py", line 245, in initialize
      self.migrate_config()
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/jupyter_core/application.py", line 170, in migrate_config
      migrate()
   File "/home/shubhamdutta/.local/lib/python3.5/site-packages/jupyter_core/migrate.py", line 247, in migrate
      with open(os.path.join(env['jupyter_config'], 'migrated'), 'w') as f:
   PermissionError: [Errno 13] Permission denied: '/home/shubhamdutta/Applications/Package_install/root-6.26.10/etc/notebook/migrated'
   ```
   CAUSE: The cause of the error is `thisroot.sh`, which is sourced when terminal launches, sets the variables `JUPYTER_PATH` and `JUPYTER_CONFIG_DIR`. This was not    done/present in the earlier versions of ROOT. As a result, when jupyter is trying to launch it encounters a conflict. 
  
   SOLUTION: This is a stop gap solution. I have commented the lines in `thisroot.sh` that modifies `JUPYTER_PATH` and `JUPYTER_CONFIG_DIR`, thus avoiding the conflict. In    case some other issue is faced in the future by ROOT, it should be checked whether this is the cause of it or not. 
  
