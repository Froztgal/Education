# WSL

## Остановить WSL

`wsl --shutdown`

Запустить можно открытием терминала WSL-дистрибутива.

**Docker Desktop** предложит перезапуститься, нужно это сделать.

## Конфигурирование

* `.wslconfig`. Глобально во всех дистрибутивах WSL2.
  * `%UserProfile%/.wslconfig`. Путь к каталогу должен выглядеть примерно так: `C:\Users\<UserName>\.wslconfig`.
  * Нужно перезапустить необходимый дистрибутив, для применения новых настроек.
* `wsl.conf`. Для конкретного дистрибутива WSL1 или WSL2.
  * `/etc/wsl.conf`
  * Нужно перезапустить необходимый дистрибутив, для применения новых настроек.

WSL обнаружит существование этих файлов, считывает содержимое и автоматически применяет параметры конфигурации при каждом запуске WSL. Если файл отсутствует или неправильно сформирован (неправильное форматирование разметки), WSL продолжит запускаться в обычном режиме без применения параметров конфигурации.

`wsl -l --running` проверить, работает ли дистрибутив Linux (оболочка) после закрытия.

Можно настроить сколько swap, памяти и процессоров выделять для `WSL 2 VM`. <https://docs.microsoft.com/en-us/windows/wsl/wsl-config#configuration-setting-for-wslconfig>

```ini
# Settings apply across all Linux distros running on WSL 2
[wsl2]

# Limits VM memory to use no more than 4 GB, this can be set as whole numbers using GB or MB
memory=4GB

# Sets the VM to use two virtual processors
processors=2

# Sets amount of swap storage space to 8GB, default is 25% of available RAM
swap=8GB
```

## Корректная работа с продуктами JetBrains

Нужно создать файл `/etc/wsl.conf` (если его ещё нет) от пользователя `root` в дистрибутиве WSL:

* <https://devblogs.microsoft.com/commandline/automatically-configuring-wsl/>
  * Wsl.conf belongs under the path /etc/wsl.conf. If the file is not there, you can create it yourself. WSL will detect the existence of the file and will read its contents.
  * `sudo vim /etc/wsl.conf`

И прописать туда содержимое:

* <https://youtrack.jetbrains.com/issue/IDEA-277436/WSL2-and-strange-issues-with-git#focus=Comments-27-6162297.0-0>
  * In effect, issue I described is very, very rare (once pew few working days), also computer is faster and colder because enabled interop hits a lot. Of course it has some drawbacks like lack of communication from distro to Windows (ex. try login docker -> it will be not possible), but may be helpful.
  * Содержимое:

    ```ini
    [interop]
    enabled = false
    ```

Документация: <https://docs.microsoft.com/en-us/windows/wsl/wsl-config>

## Описание

WSL 2 выполняется как упрощенная виртуальная машина, поэтому используются параметры виртуализации, позволяющие управлять объемом памяти или процессорами (которые могут быть знакомы при использовании Hyper-V или VirtualBox)

Дистрибутивы, работающие как WSL 1, не будут затронуты конфигурацией `.wslconfig`, так как они не работают в качестве виртуальной машины.
