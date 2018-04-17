---
title: 列のデータ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1a716aabe137c3828adf684aec344752c288bb0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="column-data"></a>列のデータ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリのキャッシュを使用して結果セットにバインドされている各データ バッファーでバッファーを作成する**SQLBindCol**です。 これらのバッファーで構築するために、値を使用、**場所**句と位置指定をエミュレートするものを更新または delete ステートメント。 位置指定の update ステートメントが実行されるときに、データ ソースからデータをフェッチにしたときに、これらのバッファー行セットのバッファーからを更新します。  
  
 カーソル ライブラリは、行セットのバッファーからキャッシュを更新で指定された C データ型に従ってデータが転送**SQLBindCol**です。 たとえば、行セットのバッファーの C データ型が SQL_C_SLONG の場合は、カーソル ライブラリは転送 4 バイトのデータです。SQL_C_CHAR である場合と*BufferLength*が 10、カーソル ライブラリが 10 バイトのデータを転送します。 カーソル ライブラリでは、任意の型チェックや変換は、データを転送に実行されません。  
  
> [!NOTE]  
>  カーソル ライブラリが列のキャッシュを更新していない場合 **StrLen_or_IndPtr*バッファーが SQL_DATA_AT_EXEC または SQL_LEN_DATA_AT_EXEC マクロの結果には、対応する行セット内です。  
  
 ときに、列、データ ソースは空白パッド固定長文字データおよび必要に応じて 0 パッドの固定長バイナリ データを更新します。 など、データ ソースは、"Smith"として char (10) の列に"Smith"を格納します。 カーソル ライブラリでは、位置指定の update ステートメントを実行した後、キャッシュにこのデータをコピーするとき、行セットのバッファーでデータを空白パッドまたはゼロで埋め込んでされません。 そのため、必要な場合、カーソル ライブラリのキャッシュの値は、空白が埋め込まれますまたはゼロが埋め込まれること、いる必要があります空白パッドや 0 パッド行セットのバッファー内の値、位置指定の update ステートメントを実行する前にします。
