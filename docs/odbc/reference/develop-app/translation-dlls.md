---
title: "翻訳 Dll |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 284bc373cca1721ea66195115a320f5a4e53e797
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="translation-dlls"></a>翻訳の Dll
アプリケーションとデータ ソース多くの場合、異なる文字セットでデータを格納します。 ODBC では、1 つの文字セットを他のデータを変換するドライバーを使用する汎用メカニズムを提供します。 変換関数を実装する DLL で構成されて**SQLDriverToDataSource**と**SQLDataSourceToDriver**、データ ソースの間をフローさせるすべてのデータを変換するドライバーと呼ばれるドライバーです。 この DLL は、ドライバーの開発者に、アプリケーション開発者によって書き込まれることができますか、サード パーティ製です。  
  
 翻訳 DLL は、特定のデータ ソースは、そのデータ ソースのシステム情報で指定できます。詳細については、次を参照してください。[データ ソースの仕様のサブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)です。 SQL_ATTR_TRANSLATE_DLL と SQL_ATTR_TRANSLATE_OPTION 接続属性を持つ実行時に設定することもできます。  
  
 翻訳オプションは、特定の翻訳 DLL でのみ解釈できる値です。 たとえば、異なるコード ページ間 DLL の変換を平行移動、オプションはアプリケーションおよびデータ ソースで使用されるコード ページの番号を与える可能性があります。 トランスレーター DLL 翻訳オプションを使用する必要はありません。  
  
 DLL が指定されている翻訳した後は、ドライバーが読み込まれるときにし、呼び出し元アプリケーションとデータ ソースの間をフローさせるすべてのデータを変換します。 これには、すべての SQL ステートメントと、データ ソースに送信される文字パラメーターが含まれ、データ ソースからすべての文字の結果、列名、およびエラー メッセージなどの文字のメタデータを取得します。 アプリケーションがデータ ソースに接続した後に、トランスレーター DLL は、まで読み込まれていないため、接続のデータは翻訳されません。
