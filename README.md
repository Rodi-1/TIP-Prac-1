# Практическая работа 1 — HTTP-сервис с UUID

Сортов Семён Александрович, ЭФМО-01-26. Дата: 09.10.2026.

Учебный HTTP-сервис: `/hello` возвращает текст, `/user` — JSON с новым UUID, `/health` — состояние и время RFC3339. Порт задаётся через APP_PORT (по умолчанию 8080); каждый запрос записывается в лог. Требования: Go 1.22+ и Git; внешняя библиотека github.com/google/uuid v1.6.0.

## Запуск и сборка

Команды выполняются из этой папки. Каждая работа запускается отдельно: по умолчанию все используют порт 8080.

```powershell
go mod download
go run ./cmd/server
# Сборка и проверки
go build -o ./bin/server.exe ./cmd/server
go fmt ./...
go vet ./...
go test ./...
# После остановки go run
.\bin\server.exe
```

## Примеры запросов

```powershell
curl.exe -i http://localhost:8080/hello
curl.exe -i http://localhost:8080/user
curl.exe -i http://localhost:8080/health
```

## Конфигурация

```powershell
$env:APP_PORT="8081"
go run ./cmd/server
# В другом окне: curl.exe -i http://localhost:8081/hello
```

## Структура

```text
.gitignore
cmd/server/main.go
go.mod
go.sum
testing.md
bin/server.exe (собранная программа, исключена из Git)
```
