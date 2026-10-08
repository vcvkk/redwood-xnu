# xnu-redwood

Порт ядра XNU (Darwin) на **redwood** = POCO X5 Pro 5G (Snapdragon 778G / SM7325).
База: `xnu-4570.41.2` (iOS 11.3, первый хорошо документированный arm64-тег) + правки для не-Apple ARM-платформ.

## Ветки
- `redwood-port` — рабочая ветка порта (эта).

## Сборка
- **macOS/Xcode** (основной путь): `make SDKROOT=macosx ARCH_CONFIGS=ARM64 KERNEL_CONFIGS=DEVELOPMENT BUILD_WERROR=0`
  → GitHub Actions workflow `.github/workflows/build.yml` собирает автоматически на `macos-latest`,
  артефакт: `mach_kernel.development.arm64` + SHA256SUMS.
- Linux-хост — не поддерживается build-системой XNU (sysctl/sw_vers/xcrun — только macOS).

## Структура правок (по мере добавления)
- `pexpert/arm64/` — Platform Expert под SM7325 (RedwoodPE): GICv3, generic timer, GENI-UART, фреймбуфер.
- `trampoline/` (вне этого дерева, отдельный репо-каталог позже) — boot.img v4 arm64-трамплин.

## Ссылки
- HD2-лаборатория (методология): слои 0–4, BOOTLOG, BOOT-MAP, запечатанные пакеты.
- `docs/prior-art.md` в рабочем каталоге проекта (локально).
