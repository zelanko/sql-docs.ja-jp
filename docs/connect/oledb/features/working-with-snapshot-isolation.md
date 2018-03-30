---
title: スナップショット分離の使用 |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーでのスナップショット分離の使用
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], snapshot isolation
- MSOLEDBSQL, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, snapshot isolation
- SQLGetInfo function
- concurrency [OLE DB Driver for SQL Server]
- SQLSetConnectAttr function
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c33c9d2f6a12c5e43a5ee47000c4faf33b294002
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="working-with-snapshot-isolation"></a>スナップショット分離を使用した作業
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、OLTP (オンライン トランザクション処理) アプリケーションの同時実行の強化を目的として、新しく "スナップショット" 分離レベルが導入されました。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、同時実行はロックだけを基にしていました。そのため、アプリケーションによってはブロックやデッドロックなどの問題が生じることがありました。 スナップショット分離は行のバージョン管理の機能強化に依存しており、リーダーとライターのブロッキングを回避することでパフォーマンスを向上することを目的としています。  
  
 スナップショット分離の下で開始されたトランザクションは、トランザクションの開始時点のデータベース スナップショットを読み取ります。 Keyset、動的および静的サーバー カーソルの場合、スナップショット トランザクション コンテキスト内で開かれるは、シリアル化可能なトランザクション内で開かれた静的カーソルと同様のように動作します。 ただし、下にある、カーソルが開かれる場合、スナップショット分離レベルのロックは取得されません。 このファクトは、サーバーでのブロックを減らすことができます。  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server  
 SQL Server の OLE DB ドライバーがで導入されたスナップショット分離を活用するための機能強化[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。 具体的には、DBPROPSET_DATASOURCEINFO プロパティ セットと DBPROPSET_SESSION プロパティ セットへ変更が加えられています。  
  
### <a name="dbpropsetdatasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 DBPROP_SUPPORTEDTXNISOLEVELS プロパティで使用される DBPROPVAL_TI_SNAPSHOT 値が追加され、DBPROPSET_DATASOURCEINFO プロパティ セットではスナップショット分離レベルがサポートされるようになりました。 この新しい値は、データベースでバージョン管理が有効になっているかどうかにかかわらず、スナップショット分離レベルがサポートされることを示します。 次の表は、DBPROP_SUPPORTEDTXNISOLEVELS の値を示します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|型 : VT_I4<br /><br /> R/W: 読み取り専用<br /><br /> 説明 : サポートされるトランザクション分離レベルを指定するビットマスク。 次の値を 0 個以上指定できます。<br /><br /> DBPROPVAL_TI_CHAOS <br /><br /> DBPROPVAL_TI_READUNCOMMITTED <br /><br /> DBPROPVAL_TI_BROWSE <br /><br /> DBPROPVAL_TI_CURSORSTABILITY <br /><br /> DBPROPVAL_TI_READCOMMITTED <br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropsetsession"></a>DBPROPSET_SESSION  
 DBPROP_SESS_AUTOCOMMITISOLEVELS プロパティで使用される DBPROPVAL_TI_SNAPSHOT 値が追加され、DBPROPSET_SESSION プロパティ セットではスナップショット分離レベルがサポートされるようになりました。 この新しい値は、データベースでバージョン管理が有効になっているかどうかにかかわらず、スナップショット分離レベルがサポートされることを示します。 次の表は、DBPROP_SESS_AUTOCOMMITISOLEVELS の値を示します。
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|型 : VT_I4<br /><br /> R/W: 読み取り専用<br /><br /> 説明 : 自動コミット モードのときのトランザクション分離レベルを示すビットマスクを指定します。 このビットマスク内に設定できる値は、DBPROP_SUPPORTEDTXNISOLEVELS に設定できる値と同じです。|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] を使用しているときに DBPROPVAL_TI_SNAPSHOT を設定すると、エラー DB_S_ERRORSOCCURRED または DB_E_ERRORSOCCURRED が発生します。  
  
 トランザクションでスナップショット分離をサポートする方法については、次を参照してください。[ローカル トランザクションのサポート](../../oledb/ole-db-transactions/supporting-local-transactions.md)です。  

  
## <a name="see-also"></a>参照  
 [SQL Server 機能の OLE DB ドライバー](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [行セットのプロパティと動作](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
