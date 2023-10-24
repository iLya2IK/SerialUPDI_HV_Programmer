# SerialUPDI_HV_Programmer

Простой программатор UPDI с функцией запуска протокола UPDI высоковольтным импульсом 12V. Последовательность сигналов для такого программирования приведена в разделе любого даташита к avr. Например:
[33.3.2.2 UPDI Enable with 12V Override of RESET pin](https://ww1.microchip.com/downloads/en/DeviceDoc/40001912A.pdf)

Инициализация протокола UPDI за счет подачи импульса высокого напряжения (12V) на пин UPDI/RESET предназначена для разблокировки устройства (в основном, типа Attiny), для которого данный пин был ранее запрограммирован на ввод-вывод и более не реагирует на программаторы другого типа (без импульса высокого напряжения).

Устройство разработано на основе схемы [SerialUPDI HV Programmer based on CH340E and MT360](https://github.com/wagiminator/AVR-Programmer/blob/master/SerialUPDI_HV_Programmer). Основные отличия:
1. Используется понижающий преобразователь напряжения NCP1529A для снижения напряжения от 5 В до 3.3 В
2. Вместо переключателя флажкового типа используется простая перемычка
3. Разъем USB поверхностного монтажа переделан в разъем типа JST XH2.54
4. В целях упрощения ручной пайки используются более крупные SMD компоненты форм-фактора 1206 для емкостей и 0805 для резисторов

![updi_hv_reset_top.png](https://raw.githubusercontent.com/iLya2IK/SerialUPDI_HV_Programmer/main/images/updi_hv_reset_top.png)
![updi_hv_reset_btm.png](https://raw.githubusercontent.com/iLya2IK/SerialUPDI_HV_Programmer/main/images/updi_hv_reset_btm.png)

Устройство собрано и протестировано. Для программирования использовал утилиту [Pure-C utility for programming AVR devices with UPDI interface using a standard TTL serial port](https://github.com/Polarisru/updiprog). Удалось записать hex файл, выставить/сбросить фьюзы с заблокированным пином UPDI.

![updi_hv_reset_photo1.jpg](https://raw.githubusercontent.com/iLya2IK/SerialUPDI_HV_Programmer/main/images/updi_hv_reset_photo1.jpg)
![updi_hv_reset_photo2.jpg](https://raw.githubusercontent.com/iLya2IK/SerialUPDI_HV_Programmer/main/images/updi_hv_reset_photo2.jpg)
![updi_hv_reset_photo2.jpg](https://raw.githubusercontent.com/iLya2IK/SerialUPDI_HV_Programmer/main/images/updi_hv_reset_box.jpg)

# References and copyrights
* [ATtiny214/414/814. Datasheet Preliminary](https://ww1.microchip.com/downloads/en/DeviceDoc/40001912A.pdf)
* [SerialUPDI HV Programmer based on CH340E and MT360](https://github.com/wagiminator/AVR-Programmer/blob/master/SerialUPDI_HV_Programmer)
* [Pure-C utility for programming AVR devices with UPDI interface using a standard TTL serial port](https://github.com/Polarisru/updiprog)
* Copyright (c) 2023, Ilya Medvedkov
