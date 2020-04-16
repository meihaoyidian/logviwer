### 实时查看日志

##### 介绍

- adb连接手机，实时查看logcat日志
- 节省配置logcat
- 可参数化配置
- 可直接测试埋点

##### Log等级

- Log.v：这里的v代表Verbose，对应的log等级为VERVOSE。采用该等级的log，任何消息都会输出
- Log.d：这里的d代表Debug调试的意思，对应的log等级为DEBUG。采用该等级的log，除了VERBOSE级别的log外，剩余的4个等级的log都会被输出
- Log.i：这里的i代表information，为一般提示性的消息，对应的log等级为INFO。采用该等级的log，不会输出VERBOSE和DEBUG信息，只会输出剩余3个等级的信息
- Log.w：w代表warning警告信息，一般用于系统提示开发者需要优化android代码等场景，对应的等级为WARN。该级别log，只会输出WARN和ERROR的信息
- Log.e：e代表error错误信息，一般用于输出异常和报错信息。该级别的log，只会输出该级别信息。一般Android系统在输出crassh等致命信息的时候，都会采用该级别的log

##### 使用方式一
```
# 执行loger.py
python loger.py xxxx(应用包名)
```

##### 拓展
```
# 获取应用包名
adb shell dumpsys activity top | awk -F " " '/TASK/ {print $2}'

# 过滤日志等级信息，--min-level('V', 'D', 'I', 'W', 'E', 'F', 'v', 'd', 'i', 'w', 'e', 'f')，不区分大小写
python loger.py xxx(应用包名) --min-level "E"
```