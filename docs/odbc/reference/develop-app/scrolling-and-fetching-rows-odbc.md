---
title: "スクロールとフェッチ (ODBC) の行 |Microsoft ドキュメント"
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
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 304baeafe4918433ab5c9495d54e4cd8970eb628
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="scrolling-and-fetching-rows-odbc"></a>スクロールとフェッチ (ODBC) の行
スクロール可能なカーソルを使用するときにアプリケーションを呼び出す**SQLFetchScroll** cursor および fetch の行を配置します。 **SQLFetchScroll**相対スクロールをサポートしています (次へ、prior、relative  *n* 行)、スクロールの絶対 (first、last、および行の *n* )、およびブックマークを配置します。 *FetchOrientation*と*FetchOffset*引数**SQLFetchScroll**次の図に示すようをフェッチする行セットを指定します。  
  
 ![次に、前に、最初と最後の行セットのフェッチ](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **次に、前に、最初と最後の行セットのフェッチ**  
  
 ![絶対、相対パス、およびブックマークが付けられた行セットをフェッチ](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **絶対、相対パス、およびブックマークが付けられた行セットのフェッチ**  
  
 **SQLFetchScroll**指定された行にカーソルを配置し、その行で始まる行セットに行を返します。 指定した行セットには、結果セットの末尾が重なっている場合、部分的な行セットが返されます。 重なっている場合、結果の先頭は、指定した行セットの設定、結果の最初の行セット通常セットが返されます。詳細については、次を参照してください。、 [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)関数の説明。  
  
 場合によっては、アプリケーションがすべてのデータを取得せずにカーソルを置きしようとする可能性があります。 たとえば、だけ、ネットワーク経由で他のデータを開かず、行のブックマークを取得したりする行が存在するかどうかをテスト目的の可能性があります。 これを行うには、SQL_ATTR_RETRIEVE_DATA ステートメント属性を SQL_RD_OFF に設定します。 このステートメント属性の設定に関係なく、ブックマーク列 (存在する場合) にバインドされた変数が常に更新されました。  
  
 アプリケーションが呼び出すことができます、行セットが取得された後に**SQLSetPos**を行セットまたは更新の行、行セットに特定の行に配置します。 使用する方法についての**SQLSetPos**を参照してください[SQLSetPos でのデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)です。  
  
> [!NOTE]  
>  スクロールは、ODBC 2 でサポートされます。*x*によってドライバー **SQLExtendedFetch**です。 詳細については、次を参照してください。[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。
