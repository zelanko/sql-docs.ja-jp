---
title: テーブル値パラメーター (OLE DB) |Microsoft ドキュメント
description: テーブル値パラメーター (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 91478e575fdde15b6bbd1f82185f7c32d5e38daa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameters-ole-db"></a>テーブル値パラメーター (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このセクションでは、SQL Server の OLE DB ドライバーでテーブル値パラメーターのサポートについて説明します。 その他の概要については、次を参照してください。[テーブル値パラメーター &#40;OLE DB Driver for SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)です。 サンプルについては、次を参照してください。[テーブル値パラメーターの&#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)です。  
  
## <a name="remarks"></a>解説  
 パラメーターのセットを使用してプロシージャにパラメーターとしてサーバーに複数行データを送信する現在のところ、(の DBPARAMS パラメーター **icommand::execute**)。 パラメーター セットを使用する場合、セットの各要素は、個別のリモート プロシージャ コール (RPC) の要求でサーバーに送信する必要があります。 テーブル値パラメーターの機能は似ていますが、サーバーとの統合はより緊密になっています。 RPC 要求の数を削減し、サーバーでセットベースの操作を有効にします。  
  
 テーブル値パラメーターは、OLE DB として SQL Server の OLE DB ドライバーでサポートされて**行セット**オブジェクト。 どの**行セット**オブジェクトでしたによって提供されるコンシューマー (つまり、SQL Server の OLE DB Driver を使用してクライアント アプリケーション) のプレース ホルダーとしてテーブル値パラメーターのパラメーターです。 テーブル値パラメーターは、他の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パラメーターの型と同じように扱われます。 SQL Server の OLE DB Driver は、作成、探索、仕様、バインディング、およびスキーマのインターフェイスを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [テーブル値パラメーターの行セットの作成](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [テーブル値パラメーターの型探索](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [テーブル値パラメーターを含むコマンドの実行](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [テーブル値パラメーターへのデータの挿入](../../oledb/ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット](../../oledb/ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [OLE DB テーブル値パラメーターの型のサポート](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [OLE DB テーブル値パラメーターの型のサポート&#40;メソッド&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [OLE DB テーブル値パラメーターの型のサポート&#40;プロパティ&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server プログラミング用の OLE DB ドライバー](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
