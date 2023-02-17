#!/bin/sh

fixhosts(){
cat > /etc/hosts << \EOF
127.0.0.1	localhost
::1		localhost
127.0.0.1	DS120j
::1		DS120j

52.84.166.71 api.themoviedb.org
52.84.166.68 api.themoviedb.org
18.65.159.31 api.themoviedb.org
13.35.0.128 api.themoviedb.org
99.84.238.181 image.tmdb.org
13.226.254.58 image.tmdb.org
65.8.164.121 image.tmdb.org
54.192.73.28 image.tmdb.org
EOF
}

rc_local_func(){
if [ "$1" = "120bak" ]; then
  rm /etc/rc.local
  if [ -f /etc/rc.local.bak ]; then
    mv -f /etc/rc.local.bak /etc/rc.local
  fi
else
  if [ -f /etc/rc.local ]; then
    mv -f /etc/rc.local /etc/rc.local.bak
  fi
  cat > /etc/rc.local << \EOF
#!/bin/sh
if [ "$1" = "R" ]
then
i2cset -y -f 0 0x45 0x00 0x55
i2cset -y -f 0 0x45 0x01 0x01
i2cset -y -f 0 0x45 0x31 0x03
i2cset -y -f 0 0x45 0x32 0x03
i2cset -y -f 0 0x45 0x33 0x03
i2cset -y -f 0 0x45 0x30 0x07
i2cset -y -f 0 0x45 0x34 128
i2cset -y -f 0 0x45 0x35 0
i2cset -y -f 0 0x45 0x36 0

killall -9 synoscsitmonitor
sleep 60
/usr/sbin/ntpdate -u ntp1.aliyun.com
systemctl stop pkg-scsit-monitor.service

fi

if [ "$1" = "G" ]
then
i2cset -y -f 0 0x45 0x00 0x55
i2cset -y -f 0 0x45 0x01 0x01
i2cset -y -f 0 0x45 0x31 0x03
i2cset -y -f 0 0x45 0x32 0x03
i2cset -y -f 0 0x45 0x33 0x03
i2cset -y -f 0 0x45 0x30 0x07
i2cset -y -f 0 0x45 0x34 0
i2cset -y -f 0 0x45 0x35 128
i2cset -y -f 0 0x45 0x36 0

killall -9 synoscsitmonitor
sleep 60
/usr/sbin/ntpdate -u ntp1.aliyun.com
systemctl stop pkg-scsit-monitor.service

fi

if [ "$1" = "B" ]
then
i2cset -y -f 0 0x45 0x00 0x55
i2cset -y -f 0 0x45 0x01 0x01
i2cset -y -f 0 0x45 0x31 0x03
i2cset -y -f 0 0x45 0x32 0x03
i2cset -y -f 0 0x45 0x33 0x03
i2cset -y -f 0 0x45 0x30 0x07
i2cset -y -f 0 0x45 0x34 0
i2cset -y -f 0 0x45 0x35 0
i2cset -y -f 0 0x45 0x36 128

killall -9 synoscsitmonitor
sleep 60
/usr/sbin/ntpdate -u ntp1.aliyun.com
systemctl stop pkg-scsit-monitor.service

fi

if [ "$1" = "W" ]
then
i2cset -y -f 0 0x45 0x00 0x55
i2cset -y -f 0 0x45 0x01 0x01
i2cset -y -f 0 0x45 0x31 0x03
i2cset -y -f 0 0x45 0x32 0x03
i2cset -y -f 0 0x45 0x33 0x03
i2cset -y -f 0 0x45 0x30 0x07
i2cset -y -f 0 0x45 0x34 128
i2cset -y -f 0 0x45 0x35 128
i2cset -y -f 0 0x45 0x36 128

killall -9 synoscsitmonitor
sleep 60
/usr/sbin/ntpdate -u ntp1.aliyun.com
systemctl stop pkg-scsit-monitor.service

fi

if [ "$1" = "" ]
then
i2cset -y -f 0 0x45 0x00 0x55
i2cset -y -f 0 0x45 0x01 0x01
i2cset -y -f 0 0x45 0x30 0x07
        
i2cset -y -f 0 0x45 0x31 0x72
i2cset -y -f 0 0x45 0x32 0x72
i2cset -y -f 0 0x45 0x33 0x72
        
i2cset -y -f 0 0x45 0x37 0x44  
i2cset -y -f 0 0x45 0x3a 0x55
i2cset -y -f 0 0x45 0x3d 0x66      

i2cset -y -f 0 0x45 0x38 0x44
i2cset -y -f 0 0x45 0x3b 0x55
i2cset -y -f 0 0x45 0x3e 0x66
i2cset -y -f 0 0x45 0x39 0x40
i2cset -y -f 0 0x45 0x3c 0x40
i2cset -y -f 0 0x45 0x3f 0x40

i2cset -y -f 0 0x45 0x34 128
i2cset -y -f 0 0x45 0x35 128
i2cset -y -f 0 0x45 0x36 128

killall -9 synoscsitmonitor
sleep 60
/usr/sbin/ntpdate -u ntp1.aliyun.com
systemctl stop pkg-scsit-monitor.service

fi

if [ "$1" = "X" ]
then
i2cset -y -f 0 0x45 0x00 0x55

killall -9 synoscsitmonitor
sleep 60
/usr/sbin/ntpdate -u ntp1.aliyun.com
systemctl stop pkg-scsit-monitor.service

fi

EOF
  if [ "$1" = "120x" ]; then
    cat >> /etc/rc.local << \EOF
if [ "$1" = "K" ]
then
/usr/bin/systemctl --force poweroff
i2cset -y -f 0 0x45 0x00 0x55
i2cset -y -f 0 0x45 0x01 0x01
i2cset -y -f 0 0x45 0x31 0x33
i2cset -y -f 0 0x45 0x32 0x33
i2cset -y -f 0 0x45 0x33 0x33
i2cset -y -f 0 0x45 0x30 0x07
i2cset -y -f 0 0x45 0x34 128
i2cset -y -f 0 0x45 0x35 0
i2cset -y -f 0 0x45 0x36 0
fi
EOF
  fi
  if [ "$1" = "120d" ]; then
    cat >> /etc/rc.local << \EOF
if [ "$1" = "K" ]
then
i2cset -y -f 0 0x45 0x77 0xc6
sleep 1
reboot
fi
EOF
  fi
  chmod 755 /etc/rc.local
fi
}

if [ "$1" = "" ]
then
  echo -e "\e[1;33m 如果一直失败，可能是引导方式不同，请另寻高明。  \e[0m"
  echo -e "\e[1;31m =================== LonelyGod =================== \e[0m"
  echo -e "\e[1;31m |                                               | \e[0m"
  echo -e "\e[1;31m |          猫盘群晖DSM7.0三合一修复脚本         | \e[0m"
  echo -e "\e[1;31m |                                               | \e[0m"
  echo -e "\e[1;31m ================= https://hin.cool ================= \e[0m"
  echo -e "\e[1;33m             bash bug 120x/120d/120bak             \e[0m"
fi

if [ "$1" = "120x" -o "$1" = "120d" ]; then
  echo -e "\e[1;33m 如果一直失败，可能是引导方式不同，请另寻高明。  \e[0m"
  echo -e "\e[1;31m =================== LonelyGod =================== \e[0m"
  echo -e "\e[1;31m |                                               | \e[0m"
  echo -e "\e[1;31m |          猫盘群晖DSM7.0三合一修复脚本         | \e[0m"
  echo -e "\e[1;31m |                                               | \e[0m"
  echo -e "\e[1;31m ================= https://hin.cool ================= \e[0m"
  rc_local_func $1
  fixhosts
  rm -rf /var/log/*

  sed -i 's#/dev/null#/tmp/scemd.log#g' /etc.defaults/syslog-ng/patterndb.d/scemd.conf
  sed -i 's#/dev/null#/tmp/postgresql.log#g' /etc.defaults/syslog-ng/patterndb.d/postgresql.conf
  sed -i 's#/var/log/scemd.log#/tmp/scemd.log#g' /etc.defaults/syslog-ng/patterndb.d/scemd.conf
  sed -i 's#/var/log/postgresql.log#/tmp/postgresql.log#g' /etc.defaults/syslog-ng/patterndb.d/postgresql.conf
  sed -i 's#/usr/bin/systemctl --force poweroff#/etc/rc.local K#g' /usr/lib/systemd/system/systemd-poweroff.service

  sed -i 's/buzzeroffcfg="0x00"/buzzeroffcfg="0x1b"/g' /etc.defaults/synoinfo.conf
  sed -i 's/enable_fan_debug="0x0"/enable_fan_debug="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_auto_poweron="yes"/support_auto_poweron="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_buzzer="yes"/support_buzzer="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_fan="yes"/support_fan="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_fan_adjust_dual_mode="yes"/support_fan_adjust_dual_mode="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_led_behavior_v2="yes"/support_led_behavior_v2="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_power_recovery="yes"/support_power_recovery="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_wol="yes"/support_wol="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/supportrcpower="yes"/supportrcpower="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/supportsystemperature="yes"/supportsystemperature="no"/g' /etc.defaults/synoinfo.conf
  sed -i 's/supportsystempwarning="yes"/supportsystempwarning="no"/g' /etc.defaults/synoinfo.conf
  echo -e "\e[1;33m 成功啦！成功啦！成功啦！立即重启猫盘，Enjoy  it!  \e[0m"
  rm -f /root/bug
  i2cset -y -f 0 0x45 0x00 0x55
  i2cset -y -f 0 0x45 0x01 0x01
  i2cset -y -f 0 0x45 0x31 0x33
  i2cset -y -f 0 0x45 0x32 0x33
  i2cset -y -f 0 0x45 0x33 0x33
  i2cset -y -f 0 0x45 0x30 0x07
  i2cset -y -f 0 0x45 0x34 0
  i2cset -y -f 0 0x45 0x35 128
  i2cset -y -f 0 0x45 0x36 0
fi

if [ "$1" = "120bak" ]; then
  echo -e "\e[1;33m 如果一直失败，可能是引导方式不同，请另寻高明。  \e[0m"
  echo -e "\e[1;31m =================== LonelyGod =================== \e[0m"
  echo -e "\e[1;31m |                                               | \e[0m"
  echo -e "\e[1;31m |          猫盘群晖DSM7.0三合一修复脚本         | \e[0m"
  echo -e "\e[1;31m |                                               | \e[0m"
  echo -e "\e[1;31m ================= https://hin.cool ================= \e[0m"

  rc_local_func $1
  rm -rf /var/log/*

  sed -i 's#/dev/null#/var/log/scemd.log#g' /etc.defaults/syslog-ng/patterndb.d/scemd.conf
  sed -i 's#/dev/null#/var/log/postgresql.log#g' /etc.defaults/syslog-ng/patterndb.d/postgresql.conf
  sed -i 's#/tmp/scemd.log#/var/log/scemd.log#g' /etc.defaults/syslog-ng/patterndb.d/scemd.conf
  sed -i 's#/tmp/postgresql.log#/var/log/postgresql.log#g' /etc.defaults/syslog-ng/patterndb.d/postgresql.conf
  sed -i 's#/etc/rc.local K#/usr/bin/systemctl --force poweroff#g' /usr/lib/systemd/system/systemd-poweroff.service

  sed -i 's/buzzeroffcfg="0x1b"/buzzeroffcfg="0x00"/g' /etc.defaults/synoinfo.conf
  sed -i 's/enable_fan_debug="no"/enable_fan_debug="0x0"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_auto_poweron="no"/support_auto_poweron="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_buzzer="no"/support_buzzer="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_fan="no"/support_fan="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_fan_adjust_dual_mode="no"/support_fan_adjust_dual_mode="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_led_behavior_v2="no"/support_led_behavior_v2="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_power_recovery="no"/support_power_recovery="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/support_wol="no"/support_wol="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/supportrcpower="no"/supportrcpower="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/supportsystemperature="no"/supportsystemperature="yes"/g' /etc.defaults/synoinfo.conf
  sed -i 's/supportsystempwarning="no"/supportsystempwarning="yes"/g' /etc.defaults/synoinfo.conf
  echo -e "\e[1;33m 成功啦！成功啦！成功啦！立即重启猫盘，Enjoy  it!  \e[0m"
  rm -f /root/bug
  i2cset -y -f 0 0x45 0x00 0x55
  i2cset -y -f 0 0x45 0x01 0x01
  i2cset -y -f 0 0x45 0x31 0x33
  i2cset -y -f 0 0x45 0x32 0x33
  i2cset -y -f 0 0x45 0x33 0x33
  i2cset -y -f 0 0x45 0x30 0x07
  i2cset -y -f 0 0x45 0x34 0
  i2cset -y -f 0 0x45 0x35 128
  i2cset -y -f 0 0x45 0x36 0
fi
/usr/bin/systemctl daemon-reload
