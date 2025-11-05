Every worker (Pod) needs information to do their job — things like:
Which database to connect to
What port to use
Passwords or API keys
But you don’t want to hardcode that info inside every worker’s manual (Pod definition).
That’s where ConfigMaps and Secrets come in!

###🧩 ConfigMap = Company Notice Board 🪧 (Non-secret info)

Every department in a company might have a notice board listing important information — like:

Office WiFi name

Meeting times

Department extensions

All employees can read it — it’s not confidential, but it’s still useful.

Similarly, a ConfigMap stores configuration data that your Pods can read and use, such as:

App settings

Database URLs

Environment variables


Instead of hardcoding that inside the Pod, you put it on the notice board:

apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  DATABASE_HOST: db.company.local
  DATABASE_PORT: "5432"



Then the Pod just looks up the board whenever it needs that info.
