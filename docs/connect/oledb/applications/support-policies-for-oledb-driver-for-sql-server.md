---
title: SQL Server の OLE DB ドライバーのサポート ポリシー |Microsoft ドキュメント
description: OLE DB driver for SQL Server サポート ポリシー
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dfac5b5acd86c71787e3ee5052927d7d59969f8b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>OLE DB driver for SQL Server サポート ポリシー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  この記事では、さまざまなデータ アクセス コンポーネントは、SQL Server の OLE DB ドライバーで使用できますについて説明します。  

## <a name="server-support"></a>サーバー サポート  
 OLE DB Driver for SQL Server への接続をサポートしている[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]、[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]、 [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)]、および[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]です。

## <a name="supported-operating-system-versions"></a>サポートされるオペレーティング システムのバージョン  
 次の表には、サポートするオペレーティング システム OLE DB Driver for SQL Server が一覧表示します。  

|サポートされるオペレーティング システム|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>ADO サポート ポリシー  
 ADO アプリケーションでは、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降の機能を必要としない場合に、Windows に付属している SQLOLEDB OLE DB プロバイダーを使用できます。  

 ADO アプリケーションは、SQL Server の OLE DB Driver を使用することができますが、指定する必要があるときは、場合`DataTypeCompatibility=80`接続文字列にします。 `DataTypeCompatibility=80` が接続文字列に含まれている場合は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の機能しか使用できません。  

## <a name="ole-db-support-policies"></a>OLE DB サポート ポリシー  
アプリケーションでは、Windows オペレーティング システムに付属の OLE DB プロバイダー (SQLOLEDB) を使用できます。 ただしをメンテナンス モードでは、更新されなくなります。 必要がありますを使用して OLE DB ドライバーの SQL Server (MSOLEDBSQL)。

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
