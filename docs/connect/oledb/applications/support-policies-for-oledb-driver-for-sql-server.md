---
title: OLE DB Driver for SQL Server のサポート ポリシー | Microsoft Docs
description: OLE DB Driver for SQL Server のサポート ポリシー
ms.date: 05/25/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7e4b77a700d494f1ed8f11a0004c60b37c5cc361
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007045"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のサポート ポリシー
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

この記事では、さまざまなデータ アクセス コンポーネントを、OLE DB Driver for SQL Server で使用する方法について説明します。  

## <a name="sql-version-support"></a>SQL バージョンのサポート  

OLE DB Driver for SQL Server は、次のバージョンの SQL Server でテストされ、これらへの接続がサポートされています。

| ドライバーのバージョン | Azure SQL データベース | Azure SQL DW | Azure SQL Managed Instance | SQL Server 2019 | SQL Server 2017 | SQL Server 2016 | SQL Server 2014 | SQL Server 2012 |
|----|-|-|-|-|-|-|-|-|
|18.4|Y|Y|Y|Y|Y|Y|Y|Y|
|18.3|Y|Y|Y|Y|Y|Y|Y|Y|
|18.2|Y|Y|Y|Y|Y|Y|Y|Y|
|18.1|Y|Y|Y| |Y|Y|Y|Y|
|18.0|Y|Y|Y| |Y|Y|Y|Y|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="supported-operating-system-versions"></a>サポートされるオペレーティング システムのバージョン  

次の表に、OLE DB Driver for SQL Server でサポートされているオペレーティング システムの一覧を示します。  

| ドライバーのバージョン | Windows Server 2019 | Windows Server 2016 | Windows Server 2012<sup>1</sup> | Windows Server 2012 R2<sup>2</sup> | Windows 10 | Windows 8.1<sup>3</sup> |
|----|-|-|-|-|-|-|
|18.4|Y|Y|Y|Y|Y|Y|
|18.3|Y|Y|Y|Y|Y|Y|
|18.2|Y|Y|Y|Y|Y|Y|
|18.1| |Y|Y|Y|Y|Y|
|18.0| |Y|Y|Y|Y|Y|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061) を使用することで、Windows Server 2012 でサポートされます。  
<sup>2</sup> [2014 年 4 月の更新プログラム](https://go.microsoft.com/fwlink/?linkid=2073785)と [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061) を使用することで、Windows Server 2012 R2 でサポートされます。  
<sup>3</sup> [2014 年 4 月の更新プログラム](https://go.microsoft.com/fwlink/?linkid=2073785)と [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061) を使用することで、Windows 8.1 でサポートされます。  

## <a name="ado-support-policies"></a>ADO サポート ポリシー  

ADO アプリケーションでは、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降の機能を必要としない場合に、Windows に付属している SQLOLEDB OLE DB プロバイダーを使用できます。  

ADO アプリケーションでは OLE DB Driver for SQL Server を使用できますが、その場合は、接続文字列に `DataTypeCompatibility=80` を指定する必要があります。 `DataTypeCompatibility=80` が接続文字列に含まれている場合は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の機能しか使用できません。  

## <a name="ole-db-support-policies"></a>OLE DB サポート ポリシー  

アプリケーションは Windows オペレーティング システムに付属している OLE DB プロバイダー (SQLOLEDB) を使用することができます。 ただし、これはメンテナンス モードになっていて、更新されなくなっています。 代わりに OLE DB Driver for SQL Server (MSOLEDBSQL) を使用してください。

## <a name="see-also"></a>関連項目  

[OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)
