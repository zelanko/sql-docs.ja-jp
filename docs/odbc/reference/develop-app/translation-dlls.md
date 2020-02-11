---
title: Translation Dll |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 168b7b5ef6f8b88a39dbbb0942cf1520adf261e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086033"
---
# <a name="translation-dlls"></a>トランザクション DLL
多くの場合、アプリケーションとデータソースは異なる文字セットにデータを格納します。 ODBC では、ドライバーが文字セット間でデータを変換できるようにするための汎用的なメカニズムが用意されています。 これは、変換関数**SQLDriverToDataSource**と**sqldatasourcetodriver**を実装する DLL で構成されます。これは、データソースとドライバー間のすべてのデータフローを変換するためにドライバーによって呼び出されます。 この DLL は、アプリケーション開発者、ドライバー開発者、またはサードパーティが記述できます。  
  
 特定のデータソースの翻訳 DLL は、そのデータソースのシステム情報で指定できます。詳細については、「[データソースの指定サブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)」を参照してください。 また、SQL_ATTR_TRANSLATE_DLL と SQL_ATTR_TRANSLATE_OPTION の接続属性を使用して、実行時に設定することもできます。  
  
 Translation オプションは、特定の翻訳 DLL でのみ解釈できる値です。 たとえば、翻訳 DLL が異なるコードページ間で変換を行う場合、オプションによって、アプリケーションとデータソースで使用されるコードページの数が指定されることがあります。 翻訳 DLL で翻訳オプションを使用する必要はありません。  
  
 変換 DLL を指定すると、ドライバーはそれを読み込み、それを呼び出して、アプリケーションとデータソース間のすべてのデータフローを変換します。 これには、データソースに送信されるすべての SQL ステートメントと文字パラメーター、すべての文字の結果、列名などの文字のメタデータ、データソースから取得されるエラーメッセージが含まれます。 変換 DLL は、アプリケーションがデータソースに接続されるまで読み込まれないため、接続データは変換されません。
