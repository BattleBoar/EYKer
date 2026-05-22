# EYKer

**EYKer** — это монолитное 64-битное ядро операционной системы EYOS.  
Обеспечивает управление памятью, процессами, драйверами и системными вызовами.

> EYKer — сердце EYOS. EYOS = SUE/EYKer

* **Языки:** C, NASM/GAS 
* **Архитектура:** x86_64 
* **Разрядность:** 64-bit
* **Структура ядра:** Монолитное

## Структура ядра

- `src/arch/x86/` — архитектурно-зависимый код:
     - Entry Point
     - GDT, IDT, TSS
- `src/core/` — ядро:
     -  процессы,
     -  память,
     -  синхронизация,
     -  kmain.
- `src/elib/` — библиотека (`memcpy`, `memset`, `strlen`).
- `src/include/` — публичные заголовки.
- `src/sd/` — стандартные драйвера:
    - COM 
    - PS/2_KM
    - VGA 
    - APIC
    - PIC
    - ATA
    - PCI
    - Serial 
- `src/sfs/` — - `src/sfs/` — системная подсистема управления файлами:
    - VFS (единый интерфейс для драйверов ФС)
    - RamFS (файловая система в памяти)
    - Загрузчик носителя (определение ФС на диске)
    - Общая логика (пути, каталоги, права).
- `src/syscall/` — системные вызовы.
- `src/unix/` — POSIX, ELF, динамические библиотеки.

### Зависимости

| Дистрибутив | Команда |
|-------------|---------|
| Arch-Base   | `sudo pacman -S base-devel nasm gcc git cmake xorriso mtools` |
| Debian-Base | `sudo apt install build-essential nasm gcc git cmake xorriso mtools` |
| Fedora-Base   | `sudo dnf groupinstall "Development Tools" && sudo dnf install nasm gcc git cmake xorriso mtools` |

Вы можете использовать, изучать, распространять его в соответствии с условиями лицензиями  Apache License 2.0 (EYKer), Полный текст лицензии доступен в LICENSE и в интернете.

**Предупреждение о плагиате:**
>  Код свободен, но не присваивайте чужую работу себе. При распространении укажите ссылку на оригинальный проект.
