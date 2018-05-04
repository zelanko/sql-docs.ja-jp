---
title: メタデータの検出 |Microsoft ドキュメント
description: OLE DB Driver for SQL Server でのメタデータの検出
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4277773fd45be05980ec32b710f41ea0836315c6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="metadata-discovery"></a>メタデータの検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  メタデータ検出機能が強化[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]により、OLE DB Driver for SQL Server のアプリケーションがその列を確認またはクエリの実行から返されるパラメーター メタデータが同一にする前に指定したメタデータ形式との互換性クエリを実行します。 クエリの実行後に返されたメタデータにクエリの実行前に指定したメタデータ形式との互換性がない場合は、エラーが発生します。  
  
 Bcp および IBCPSession と IBCPSession2 インターフェイスで指定できます、遅延をクエリ出力操作のメタデータの検出を回避するのには、読み取り (遅延メタデータ検出)。 その結果、パフォーマンスが向上し、メタデータ検出のエラーを回避できます。  
  
 SQL Server の OLE DB Driver を使用してアプリケーションを開発サーバーのバージョンに接続した場合よりも前[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、メタデータ検出機能は、サーバーのバージョンに対応します。  
  
## <a name="remarks"></a>解説   
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の OLE DB メンバー関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   Icommandwithparameters::getparameterinfo (を参照してください[ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md)詳細)  
  
 IBCPSession::BCPSetBulkMode を使用してメタデータ形式を指定する場合にも、パフォーマンスを改善を表示されます。  
  
 2 つのストアド プロシージャの追加により OLE DB Driver for SQL Server での強化されたメタデータの検出が可能な[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
