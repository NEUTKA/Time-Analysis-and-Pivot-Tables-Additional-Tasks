# Проект: Проверка подключений продуктов через телемаркетинг

## Описание проекта
Проект посвящен проверке корректности подключений продуктов через телемаркетинг. Входные данные — файлы с продажами, содержащие информацию о филиале, пользователе, продукте и времени действия. Основной задачей является фильтрация данных и соединение файлов о продажах с логами по подключениям в системе, чтобы выделить успешные подключения.

## Особенности данных
1. **SUBS_ID** может быть неполным. Если идентификатор не начинается с "id", необходимо добавить префикс "id".
2. **Порядок полей** в файлах произвольный, но **названия колонок фиксированные**.
3. **Продажа не засчитывается**, если отключение (`END_DTTM`) произошло менее чем через 5 минут после подключения (`START_DTTM`).
4. **Строки без SUBS_ID** в файле с продажами игнорируются.

## Требования к результату
- Результат должен быть сохранен в **CSV-файл** с разделителем `;`.
- В результирующем файле должны содержаться только строки с корректными подключениями.

## Задачи

1. **Обработка SUBS_ID**
   - Проверить значение `SUBS_ID` для каждого подключения. Если `SUBS_ID` не начинается с "id", добавить префикс "id".

2. **Универсальный порядок колонок**
   - Обеспечить обработку файлов независимо от порядка колонок. Поля могут быть в произвольном порядке, но всегда присутствуют `FILIAL_ID`, `SUBS_ID`, `PROD_ID`, и `ACT_DTTM`.

3. **Фильтрация по времени**
   - Исключить строки, в которых время отключения (`END_DTTM`) наступает менее чем через 5 минут после времени подключения (`START_DTTM`).

4. **Исключение строк без SUBS_ID**
   - Пропускать строки, если значение `SUBS_ID` отсутствует.

## Ожидаемый результат
Файл CSV с корректными подключениями, сохранённый с разделителем `;`.


# Project: Verification of Product Connections via Telemarketing

## Project Description  
This project focuses on verifying the correctness of product connections made via telemarketing. The input data consists of sales files containing information about the branch, user, product, and activation time. The main goal is to filter the data and merge the sales files with system connection logs to identify successful connections.

## Data Features  
1. **SUBS_ID** may be incomplete. If the identifier does not start with "id," a "id" prefix must be added.  
2. **Field order** in the files is arbitrary, but **column names are fixed**.  
3. **Sales are invalid** if disconnection (`END_DTTM`) occurs less than 5 minutes after connection (`START_DTTM`).  
4. **Rows without SUBS_ID** in the sales file are ignored.

## Output Requirements  
- The result must be saved as a **CSV file** with a `;` delimiter.  
- The resulting file should only include rows with valid connections.

## Tasks  

1. **SUBS_ID Processing**  
   - Verify the value of `SUBS_ID` for each connection. If `SUBS_ID` does not start with "id," add the "id" prefix.  

2. **Arbitrary Column Order**  
   - Ensure that files are processed regardless of the column order. Fields may appear in any order, but `FILIAL_ID`, `SUBS_ID`, `PROD_ID`, and `ACT_DTTM` will always be present.  

3. **Time-Based Filtering**  
   - Exclude rows where the disconnection time (`END_DTTM`) occurs less than 5 minutes after the connection time (`START_DTTM`).  

4. **Exclude Rows Without SUBS_ID**  
   - Skip rows where `SUBS_ID` is missing.

## Expected Result  
A CSV file containing valid connections, saved with a `;` delimiter.  