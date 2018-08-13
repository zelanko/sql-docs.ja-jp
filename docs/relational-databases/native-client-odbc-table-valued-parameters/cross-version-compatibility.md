---
title: 複数バージョンの互換性 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: c53ac418f6d394fbb6bdfeacccbe5244ecae62b4
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562556"
---
# <a name="cross-version-compatibility"></a>複数バージョン間の互換性
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  バージョン間の競合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のクライアント インスタンスまたはサーバー インスタンスでテーブル値パラメーターを処理する必要がある場合に発生することがあります。  
  
 一般に、テーブル値パラメーターの機能を使用できるのは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) のサーバーに接続されている [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のクライアント (SQL Server Native Client 10.0 を使用) だけです。 カタログ関数の結果セットの新しい列はのみに接続されているときに表示されます、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (またはそれ以降) サーバー。  
  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でコンパイルされたクライアント アプリケーションで、テーブル値パラメーターが必要なステートメントを実行すると、サーバーではデータ変換エラーからこの状態が検出され、ODBC によって、これが "データ型の属性に関する制限に違反しました" というメッセージの SQLSTATE 07006 として返されます。  
  
 場合、クライアント アプリケーションでコンパイルされた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 10.0 またはサーバー インスタンスに接続されているときに、テーブル値パラメーターを使用する以降の試行よりも前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client が、これを検出し、SQLBindCol、SQLBindParameter、SQLSetDescFields、および SQLSetDescRec 呼び出しは「データ型の属性違反 (この接続の SQL Server のバージョンではテーブル値パラメーターはサポートされません) の制限」とメッセージの SQLSTATE 07006 で失敗します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
