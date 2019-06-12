---
title: OLE DB Driver for SQL Server のサポート ポリシー | Microsoft Docs
description: OLE DB Driver for SQL Server のサポート ポリシー
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 7aa291121c751b6634eed645fba52247849b6721
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778081"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のサポート ポリシー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  この記事では、さまざまなデータ アクセス コンポーネントで使える OLE DB Driver for SQL Server について説明します。  

## <a name="server-support"></a>サーバー サポート  
 OLE DB Driver for SQL Server への接続をサポートしている[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]、 [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]、 [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)]、および[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]します。

## <a name="supported-operating-system-versions"></a>サポートされるオペレーティング システムのバージョン  
 次の表には、オペレーティング システム サポートする OLE DB Driver for SQL Server が一覧表示します。  

|サポートされるオペレーティング システム|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1 + [2014 年 4 月の更新](https://go.microsoft.com/fwlink/?linkid=2073785) + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012 + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2012 R2 + [2014 年 4 月の更新](https://go.microsoft.com/fwlink/?linkid=2073785) + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>ADO サポート ポリシー  
 ADO アプリケーションでは、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降の機能を必要としない場合に、Windows に付属している SQLOLEDB OLE DB プロバイダーを使用できます。  

 ADO アプリケーションは、SQL Server の OLE DB Driver を使用することができますが、その場合を指定する必要があります`DataTypeCompatibility=80`接続文字列にします。 `DataTypeCompatibility=80` が接続文字列に含まれている場合は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の機能しか使用できません。  

## <a name="ole-db-support-policies"></a>OLE DB サポート ポリシー  
アプリケーションは Windows オペレーティング システムに付属している OLE DB プロバイダー (SQLOLEDB) を使用することができます。 ただし、メンテナンス モードにして更新されなくなります。 代わりに OLE DB Driver for SQL Server (MSOLEDBSQL) を使用します。

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
