# SMARTPBR #
## ���� ##
SmartPBRΪһ��������ά��Ա�����Զ�����װ����·�ɷ�����Ҫ��ҵʹ��LINUX���ز���·������������

##���� ##

 - ����·����·
 - �л�����

## ������� ##
    smartpbr-x.x.x          ��װĿ¼        /usr/local/smartpbr        �����ļ�    /etc/smartpbr
    
## �������� ##

    ./smartpbr install    #��װsmartpbr
    /etc/init.d/smartpbr  #��������ʽ�ű�

## �Ѳ��Ա��뻷�� ##

    Red Hat Enterprise Linux Server release 6.4 (Santiago)
    

�������������Ҫ�ֶ���װ���밴�����¹淶���а�װ

��װ�����ݣ�

    smartvpn_x.x.x
    �� smartpbr.sh                    #�Զ����ű�
    ��
    ����config                         #�����ļ���
           line                      #��·�ļ���
               ����x.config              #��·�����ļ�
           route.config                #·�������ļ�
           rule.config                 #���������ļ�

## �ֶ����� ##

1�����dxt·��

    vim /etc/iproute2/rt_tables
    252	dxt

2����ʼ��dxt·�ɱ�

    ip route flush table dxt
    #dxtΪ�����ӵ�·�ɱ�

3�����ӷ������ص�·��(�����Լ��޷���������)

    ip route add 192.168.8.0/24 via 192.168.8.253 dev eth1 table dxt
    #192.168.8.0/24:�����Լ�������,192.168.8.253Ϊ���ص�ַ,eth1 ���������,dxt����·�ɱ�

4������Ĭ��·��

    ip route add default via 124.192.224.33 dev eth0 table dxt
    #Default:����Ĭ��·��,124.192.224.33��������,eth0���������,dxt����·�ɱ�

5�����Ӳ���·��

    ip rule add from 192.168.8.0/24 table dxt
    #192.168.8.253��������IP,dxt����·�ɱ�

6���л�SNAT

    iptables -t nat -I POSTROUTING -s 192.168.8.0/24 -j SNAT --to-source 124.192.224.55 
