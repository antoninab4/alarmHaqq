# alarmHaqq
Эта система будет оповещать вас в Телеграм о джейлах, пропущенных блоках в неактивном статусе и т. д. Также она каждый час отправляет вам краткую информацию о статусе вашего узла.

                                    Инструкция:

Создаем телеграмм-бота через @BotFather, настройте его и get bot API token. Если не получается создать смотрим здесь https://www.siteguarding.com/en/how-to-get-telegram-bot-api-token
Создаем  2-е группы: alarm и log. Настраиваем их, добавьте своего бота в свои чаты и get chats IDs. Если не получается создать то смотрим здесь https://stackoverflow.com/questions/32423837/telegram-bot-how-to-get-a-group-chat-id
Подключитесь к вашему серверу и создайте status папку в $HOME directory файле mkdir $HOME/status/.
В этой папке $HOME/status/ вы должны создать cosmos.sh файл с расширением nano $HOME/status/cosmos.sh. Вам не нужно вносить какие-либо изменения в cosmos.sh файл, он готов к использованию.
Вы можете найти cosmos.sh в этом репозитории.(копируем все содержимое себе)

В этой папке $HOME/status/вы должны создать haqq.conf файл с расширением nano $HOME/status/haqq.conf. Настройте его.(ОБЯЗАТЕЛЬНО!! настраиваем свои значения)
Вы можете найти haqq.conf в этом репозитории.

Установите несколько пакетов с расширением sudo apt-get install jq sysstat bc smartmontools fdisk -y.
Запустите bash cosmos.sh, чтобы проверить настройки. Если так то все Вы настроили верно - Нормальный вывод:
root@otmorozky:~/status# bash cosmos.sh
 
exp/me >>>>>> 247490/247490.
gap >>>>>>>>> 0 blocks.
chain >>>>>>> alive.
consensus >>> 0.00.
block_time >> 6.33 sec.
priv_key >>>> right.
_active >>>>> false.
gov >>>>>>>>> no unvoted proposals.

_upgrade >>>> v1.1.0.
_time_left >> 15h 18m.
_appr_time >> Sep 27, 16:36.

root@otmorozky:~/status#
Добавьте несколько правил с помощью chmod u+x $HOME/status/cosmos.sh.
Отредактируйте crontab с помощью crontab -e.
# status
1,11,21,31,41,51 * * * * bash $HOME/status/cosmos.sh >> $HOME/status/cosmos.log 2>&1
Проверьте свои журналы с помощью cat $HOME/status/cosmos.logили tail $HOME/status/cosmos.log -f.
