## MyEMS Database

### Introduction

Providing database schema and scripts for MyEMS.


### Prerequisites

MySQL 8.0
MemSQL 7.0 (highly recommended)


### Installation

Execute  the scripts in a MySQL client tool (MySQL Workbench, Navicate, DBaver)

#### Change COLLATE for MySQL server before version 8.0
```
sudo nano /etc/mysql/my.cnf
```
```
[client]
default-character-set = utf8mb4
[mysql]
default-character-set = utf8mb4
[mysqld]
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci
```

### Database Definition

#### myems_system_db
[tbl_cost_centers](#tbl_cost_centers) | [tbl_data_sources](#tbl_data_sources)

##### tbl_cost_centers

| Name      | Type     | Length     | Allow Null | Description
| :---          |    :----:   |  :----:       |  :----:       |     :---         |
| id            |   BIGINT    |             | NOT NULL | ID
| name      | VARCHAR |     128    | NOT NULL   | 名字
| uuid       | CHAR         | 36          | NOT NULL  | UUID
| external_id   | VARCHAR | 36 |    NULL | 外部系统中的ID或标记，如SAP等ERP系统


##### tbl_data_sources

| Name      | Type     | Length     | Allow Null | Description
| :---          |    :----:   |  :----:       |  :----:       |     :---         |
| id            |   BIGINT    |              | NOT NULL | ID
| name      | VARCHAR |     128    | NOT NULL | 名字
| uuid       | CHAR         | 36          | NOT NULL | UUID
| protocol   | VARCHAR | 16        | NOT NULL | 通讯协议 ('modbus-tcp', 'modbus-tru', 'bacnet-ip', 's7', 'opc-ua', 'control-logix' )
| connection   | JSON |   |  NOT NULL | 通讯地址 JSON格式
| last_seen_datetime_utc   | DATETIME |   |  NOT NULL | 最后一次上线时间(UTC)


#### myems_historical_db

#### myems_energy_db

#### myems_billing_db

#### myems_user_db

#### myems_fdd_db

#### myems_reporting_db
