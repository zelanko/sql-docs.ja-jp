---
title: バージョン間の互換性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f23b0f43b32d737f03cb7c9b00368558e89e9288
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199995"
---
# <a name="cross-version-compatibility"></a>複数バージョン間の互換性
  バージョン間の競合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のクライアント インスタンスまたはサーバー インスタンスでテーブル値パラメーターを処理する必要がある場合に発生することがあります。  
  
 一般に、テーブル値パラメーターの機能を使用できるのは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) のサーバーに接続されている [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のクライアント (SQL Server Native Client 10.0 を使用) だけです。 カタログ関数の結果セットの新しい列は、以降の[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]サーバーに接続されている場合にのみ存在します。  
  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でコンパイルされたクライアント アプリケーションで、テーブル値パラメーターが必要なステートメントを実行すると、サーバーではデータ変換エラーからこの状態が検出され、ODBC によって、これが "データ型の属性に関する制限に違反しました" というメッセージの SQLSTATE 07006 として返されます。  
  
 Native client 10.0 以降で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンパイルされたクライアントアプリケーションが、より[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]前のサーバーインスタンスに接続したときにテーブル値パラメーターを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しようとした場合、native client はこれを検出し、SQLBindCol、SQLBindParameter、SQLSetDescFields、SQLSetDescRec の呼び出しは SQLSTATE 07006 で失敗し、メッセージ "制限付き SQL Server のデータ型属性違反 (この接続のバージョンはテーブル値パラメーターを  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
