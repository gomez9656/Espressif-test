set(srcs
    "common/esp_modbus_master.c"
    "common/esp_modbus_slave.c"
    "modbus/mb.c"
    "modbus/mb_m.c"
    "modbus/ascii/mbascii.c"
    "modbus/ascii/mbascii_m.c"
    "modbus/rtu/mbrtu_m.c"
    "modbus/rtu/mbrtu.c"
    "modbus/rtu/mbcrc.c"
    "modbus/tcp/mbtcp.c"
    "modbus/tcp/mbtcp_m.c"
    "port/port.c"
    "port/portevent.c"
    "port/portevent_m.c"
    "port/portother.c"
    "port/portother_m.c"
    "port/portserial.c"
    "port/portserial_m.c"
    "port/porttimer.c"
    "port/porttimer_m.c"
    "modbus/functions/mbfunccoils.c"
    "modbus/functions/mbfunccoils_m.c"
    "modbus/functions/mbfuncdiag.c"
    "modbus/functions/mbfuncdisc.c"
    "modbus/functions/mbfuncdisc_m.c"
    "modbus/functions/mbfuncholding.c"
    "modbus/functions/mbfuncholding_m.c"
    "modbus/functions/mbfuncinput.c"
    "modbus/functions/mbfuncinput_m.c"
    "modbus/functions/mbfuncother.c"
    "modbus/functions/mbutils.c"
    "serial_slave/modbus_controller/mbc_serial_slave.c"
    "serial_master/modbus_controller/mbc_serial_master.c"
    "tcp_slave/port/port_tcp_slave.c"
    "tcp_slave/modbus_controller/mbc_tcp_slave.c"
    "tcp_master/modbus_controller/mbc_tcp_master.c"
    "tcp_master/port/port_tcp_master.c"
    "common/esp_modbus_master_tcp.c"
    "common/esp_modbus_slave_tcp.c"
    "common/esp_modbus_master_serial.c"
    "common/esp_modbus_slave_serial.c")

set(include_dirs common/include)

set(priv_include_dirs common port modbus modbus/ascii modbus/functions
                                modbus/rtu modbus/tcp modbus/include)

list(APPEND priv_include_dirs serial_slave/port serial_slave/modbus_controller
                                        serial_master/port serial_master/modbus_controller
                                tcp_slave/port tcp_slave/modbus_controller
                                tcp_master/port tcp_master/modbus_controller)

idf_component_register(SRCS "${srcs}"
                    INCLUDE_DIRS "${include_dirs}"
                    PRIV_INCLUDE_DIRS "${priv_include_dirs}"
                    REQUIRES driver)
