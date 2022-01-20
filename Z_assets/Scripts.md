
- for /l %i in (1,1,255) do @ping -n 1 -w 100 10.1.0.%i | find /i "reply" 3A