# temp1
import random
command_list = ""
t = 1
m = 1
for i in range(30):
    sid = random.randint(1000,10000)
    command_mysql = """(sleep {} && mysql -h localhost -u root -proot -D test1 -Bse " SET profiling = 1;select * from test where store_id={};SHOW PROFILES;" >>test.txt && echo "sec 0" >> test.txt) & \
    \n""".format(m, str(sid))

    command_list += command_mysql

    if t % 2 == 0:
        m += 1
    
    t += 1

f = open("test3.sh","w+")
f.write(command_list)
