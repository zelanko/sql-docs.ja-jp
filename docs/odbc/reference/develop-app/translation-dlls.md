---
title: 翻訳 DLL |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3dad12bcd71434c1013b4fde5b4bd0231e56016f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297947"
---
# <a name="translation-dlls"></a>トランザクション DLL
アプリケーションとデータ ソースは、多くの場合、異なる文字セットにデータを格納します。 ODBC には、ドライバーがデータをある文字セットから別の文字セットに変換できるようにする汎用的なメカニズムが用意されています。 これは、データ ソースとドライバーの間で流れるすべてのデータを変換するためにドライバーによって呼び出される変換関数**SQLDriverToDataSource**と**SQLDataSourceToDriver**を実装する DLL で構成されます。 この DLL は、アプリケーション開発者、ドライバー開発者、またはサード パーティによって記述できます。  
  
 特定のデータ ソースの変換 DLL は、そのデータ ソースのシステム情報で指定できます。詳細については、「[データ ソース仕様サブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)」を参照してください。 また、SQL_ATTR_TRANSLATE_DLLとSQL_ATTR_TRANSLATE_OPTION接続属性を使用して実行時に設定することもできます。  
  
 変換オプションは、特定の変換 DLL によってのみ解釈できる値です。 たとえば、変換 DLL が異なるコード ページ間で変換される場合、このオプションは、アプリケーションとデータ ソースで使用されるコード ページの番号を指定する場合があります。 翻訳 DLL で翻訳オプションを使用する必要はありません。  
  
 変換 DLL を指定した後、ドライバーは、それを読み込み、アプリケーションとデータ ソース間で流れるすべてのデータを変換する呼び出しします。 これには、データ ソースに送信されるすべての SQL ステートメントと文字パラメーター、およびすべての文字結果、列名などの文字メタデータ、およびデータ ソースから取得されたエラー メッセージが含まれます。 変換 DLL は、アプリケーションがデータ ソースに接続するまで読み込まれないので、接続データは変換されません。
