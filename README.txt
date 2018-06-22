###############
#Configuration#
###############
cfg.txt файл настроек написанный с использование JSON нотации.
"sendersCount":<long> - число потоков  посылающий submit_sm синхронно(ускоряет отправку но грузит проц) 
"PDUToSendCount": <long> - число submit_sm'ов которые будут отправлены
"host":<String> - ip SMSC
"port":<long> - порт SMSC
"systemId":<String> - то же самое что и логин для SMSC
"password":<String> - пароль SMSC
"awaitTimer":<long> - время ожидания для получения всех деливеров по отправленны submit_sm'ам, после чего программа выполнит unbind команду, отключится от SMSC, и покажет немного статистики.
"bindParams": <JSONArray> - параметры дял команды bind
            "typeOfNumber":<String> - строка представляющая параметр addr_ton команды bind_transceiver SMPP протокола
                                    -может быть установлено в: "UNKNOWN","INTERNATIONAL","NATIONAL","NETWORK_SPECIFIC","SUBSCRIBER_NUMBER","ALPHANUMERIC","ABBREVIATED"
            "numberingPlanIndicator":<String> - строка представляющая параметр addr_npi команды bind_transceiver SMPP протокола
                                              - может быть установлено в: "UNKNOWN","ISDN","DATA","TELEX","LAND_MOBILE","NATIONAL","PRIVATE","ERMES","INTERNET","WAP"
            "addressRange":<String> - строка представляющая параметр address_range команды bind_transceiver SMPP протокола
"submitSMParams": <JSONArray> - параметры submit_sm
                "serviceType":<String> - строка представляющая параметр service_type команды submit_sm SMPP протокола
                                       - может быть установлено в : ""null,"CMT","CPT","VMN","VMA","WAP","USSD"
                "sourceAddr":<String> - строка представляющая номер телефона отправителя
                "sourceTypeOfNumber":<String> - то же самое что typeOfNumber из "bindParams" только для отправителя
                "sourceNumberingPlanIndicator":<String> - то же самое что numberingPlanIndicator из "bindParams" только для отправителя
                "destTypeOfNumber":<String> - то же самое что typeOfNumber из "bindParams" только для получателя
                "destNumberingPlanIndicator":<String> - то же самое что numberingPlanIndicator из "bindParams" только для получателя
                "sheduledDeliver":<String> - строка которая представляет параметр shedule_delivery_time submit_sm команды SMPP протокола

#######
#Usage#
#######
Настроить cfg.txt, запустить SMPPSim и нажать старт

######
#Logs#
######
Есть два файла логов:"log.txt" - лог работы программы, "info.txt" - лог доставки

######
#Bugs#
######
Эта программа не отлажена до конца, поэтому будут возникать баги такие как:
-Если параметр конфигурации sendersCount установлен в некоторое не разумное число потоков например >500, программа будет быстро отсылать submit_sm, тем самым нагружая SMSC вследствие чего будет возникать timout exception.
-Когда кнопка Старт нажимется программа может не начать отправку если предыдущее использование программы не было корректно завершено(потому что привязка сессии с SMSC была некорректна отвязана). Поэтому приходится перезапускать SMPPSim и программу.
-При переключении между Старт/Стоп может залагать отправка тк не все переменные сброшены и новая сессия открывается некорректно.
-Кнопка выход иногда не выходит=)
-Регулятор потоков не реализован



