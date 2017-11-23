---
title: "バージョン間の互換性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4dda2d778124f86681f06921e404472d266b5e41
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="cross-version-compatibility"></a>バージョン間の互換性
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  バージョン間の競合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のクライアント インスタンスまたはサーバー インスタンスでテーブル値パラメーターを処理する必要がある場合に発生することがあります。  
  
 一般に、テーブル値パラメーターの機能を使用できるのは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) のサーバーに接続されている [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のクライアント (SQL Server Native Client 10.0 を使用) だけです。 新しいカタログ関数の結果セット列にのみ表示されますへ接続している場合、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (またはそれ以降) サーバー。  
  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でコンパイルされたクライアント アプリケーションで、テーブル値パラメーターが必要なステートメントを実行すると、サーバーではデータ変換エラーからこの状態が検出され、ODBC によって、これが "データ型の属性に関する制限に違反しました" というメッセージの SQLSTATE 07006 として返されます。  
  
 場合、クライアント アプリケーションでコンパイルされた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 10.0 またはサーバー インスタンスに接続しているときに、テーブル値パラメーターを使用する以降の試行よりも前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client が、これを検出し、SQLBindCol、SQLBindParameter、SQLSetDescFields、および sqlsetdescrec による呼び出しが失敗とメッセージの SQLSTATE 07006"(この接続用の SQL Server のバージョンではテーブル値パラメーターはサポートされません) データ型の属性違反を Restricted"します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
