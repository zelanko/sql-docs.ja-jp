---
title: メタデータの検出 |Microsoft Docs
description: OLE DB Driver for SQL Server でメタデータの検出
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 3ed5020498dee14a34bd66076fc74a578bc09e69
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765970"
---
# <a name="metadata-discovery"></a>メタデータの検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ではメタデータ検出機能が強化されているため、OLE DB Driver for SQL Server アプリケーションでは、クエリの実行によって返された列またはパラメーター メタデータがクエリの実行前に指定したメタデータ形式と同じであるか、その形式と互換性があることを確認できます。 クエリの実行後に返されたメタデータにクエリの実行前に指定したメタデータ形式との互換性がない場合は、エラーが発生します。  
  
 bcp 関数と IBCPSession および IBCPSession2 インターフェイスでは、遅延読み取り (遅延メタデータ検出) を指定して、クエリ出力操作でメタデータ検出を回避できます。 その結果、パフォーマンスが向上し、メタデータ検出のエラーを回避できます。  
  
 OLE DB Driver for SQL Server を使用してアプリケーションを開発し、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] より前のバージョンのサーバーに接続する場合、メタデータ検出機能はそのバージョンのサーバーに対応したものとなります。  
  
## <a name="remarks"></a>Remarks   
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の OLE DB メンバー関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   Icommandwithparameters::getparameterinfo (を参照してください[ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md)詳細)  
  
 IBCPSession::BCPSetBulkMode を使用してメタデータ形式を指定したときのパフォーマンスも向上しています。  
  
 2 つのストアド プロシージャの追加により、OLE DB Driver for SQL Server で強化されたメタデータの検出が可能な[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
