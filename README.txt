###############
#Configuration#
###############
cfg.txt ���� �������� ���������� � ������������� JSON �������.
"sendersCount":<long> - ����� �������  ���������� submit_sm ���������(�������� �������� �� ������ ����) 
"PDUToSendCount": <long> - ����� submit_sm'�� ������� ����� ����������
"host":<String> - ip SMSC
"port":<long> - ���� SMSC
"systemId":<String> - �� �� ����� ��� � ����� ��� SMSC
"password":<String> - ������ SMSC
"awaitTimer":<long> - ����� �������� ��� ��������� ���� ��������� �� ����������� submit_sm'��, ����� ���� ��������� �������� unbind �������, ���������� �� SMSC, � ������� ������� ����������.
"bindParams": <JSONArray> - ��������� ��� ������� bind
            "typeOfNumber":<String> - ������ �������������� �������� addr_ton ������� bind_transceiver SMPP ���������
                                    -����� ���� ����������� �: "UNKNOWN","INTERNATIONAL","NATIONAL","NETWORK_SPECIFIC","SUBSCRIBER_NUMBER","ALPHANUMERIC","ABBREVIATED"
            "numberingPlanIndicator":<String> - ������ �������������� �������� addr_npi ������� bind_transceiver SMPP ���������
                                              - ����� ���� ����������� �: "UNKNOWN","ISDN","DATA","TELEX","LAND_MOBILE","NATIONAL","PRIVATE","ERMES","INTERNET","WAP"
            "addressRange":<String> - ������ �������������� �������� address_range ������� bind_transceiver SMPP ���������
"submitSMParams": <JSONArray> - ��������� submit_sm
                "serviceType":<String> - ������ �������������� �������� service_type ������� submit_sm SMPP ���������
                                       - ����� ���� ����������� � : ""null,"CMT","CPT","VMN","VMA","WAP","USSD"
                "sourceAddr":<String> - ������ �������������� ����� �������� �����������
                "sourceTypeOfNumber":<String> - �� �� ����� ��� typeOfNumber �� "bindParams" ������ ��� �����������
                "sourceNumberingPlanIndicator":<String> - �� �� ����� ��� numberingPlanIndicator �� "bindParams" ������ ��� �����������
                "destTypeOfNumber":<String> - �� �� ����� ��� typeOfNumber �� "bindParams" ������ ��� ����������
                "destNumberingPlanIndicator":<String> - �� �� ����� ��� numberingPlanIndicator �� "bindParams" ������ ��� ����������
                "sheduledDeliver":<String> - ������ ������� ������������ �������� shedule_delivery_time submit_sm ������� SMPP ���������

#######
#Usage#
#######
��������� cfg.txt, ��������� SMPPSim � ������ �����

######
#Logs#
######
���� ��� ����� �����:"log.txt" - ��� ������ ���������, "info.txt" - ��� ��������

######
#Bugs#
######
��� ��������� �� �������� �� �����, ������� ����� ��������� ���� ����� ���:
-���� �������� ������������ sendersCount ���������� � ��������� �� �������� ����� ������� �������� >500, ��������� ����� ������ �������� submit_sm, ��� ����� �������� SMSC ���������� ���� ����� ��������� timout exception.
-����� ������ ����� ��������� ��������� ����� �� ������ �������� ���� ���������� ������������� ��������� �� ���� ��������� ���������(������ ��� �������� ������ � SMSC ���� ����������� ��������). ������� ���������� ������������� SMPPSim � ���������.
-��� ������������ ����� �����/���� ����� �������� �������� �� �� ��� ���������� �������� � ����� ������ ����������� �����������.
-������ ����� ������ �� �������=)
-��������� ������� �� ����������



