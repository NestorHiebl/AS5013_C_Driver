# AS5013 STM32 HAL Driver

The code in this repo is a driver for the AS5013 miniature joystick, written in C and using the STM32 hardware abstraction layer to handle I²C communication. The driver is very basic - it allows one to query the position of the joystick, but does not encompass all possible functionality such as calibration. Still, it is well documented and easy to build on.

In case you want to adapt this driver for a different hardware abstraction library, the bulk of the work you need to do is rewrite the generic read and write functions:


```c
HAL_StatusTypeDef AS5013_generic_read_single(I2C_HandleTypeDef *hi2c, uint8_t device_register, uint8_t *read_result);
HAL_StatusTypeDef AS5013_generic_write_single(I2C_HandleTypeDef *hi2c, uint8_t device_register, uint8_t data);
```

All direct I²C interfacing takes place within their bodies.
