---
title: スクロールとフェッチ (ODBC) の行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89a83550fa7114db564ef46b83b77892d04d0e07
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913277"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>スクロールとフェッチ (ODBC) の行
スクロール可能なカーソルを使用するときにアプリケーションを呼び出す**SQLFetchScroll** cursor および fetch の行を配置します。 **SQLFetchScroll**相対スクロールをサポートしています (次へ、prior、relative *n*行)、スクロールの絶対 (first、last、および行の*n*)、およびブックマークによる位置指定します。 *FetchOrientation*と*FetchOffset*引数**SQLFetchScroll**次の図に示すようをフェッチする行セットを指定します。  
  
 ![次に、前に、最初と最後の行セットのフェッチ](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **次に、前に、最初と最後の行セットのフェッチ**  
  
 ![絶対、相対パス、およびブックマークが付けられた行セットをフェッチ](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **絶対、相対パス、およびブックマークが付けられた行セットのフェッチ**  
  
 **SQLFetchScroll**指定された行にカーソルを配置し、その行で始まる行セットに行を返します。 指定した行セットには、結果セットの末尾が重なっている場合、部分的な行セットが返されます。 重なっている場合、結果の先頭は、指定した行セットの設定、結果の最初の行セット通常セットが返されます。詳細については、次を参照してください。、 [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)関数の説明。  
  
 場合によっては、アプリケーションがすべてのデータを取得せずにカーソルを置きしようとする可能性があります。 たとえば、だけ、ネットワーク経由で他のデータを開かず、行のブックマークを取得したりする行が存在するかどうかをテスト目的の可能性があります。 これを行うには、SQL_ATTR_RETRIEVE_DATA ステートメント属性を SQL_RD_OFF に設定します。 このステートメント属性の設定に関係なく、ブックマーク列 (存在する場合) にバインドされた変数が常に更新されました。  
  
 アプリケーションが呼び出すことができます、行セットが取得された後に**SQLSetPos**を行セットまたは更新の行、行セットに特定の行に配置します。 使用する方法についての**SQLSetPos**を参照してください[SQLSetPos でのデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)です。  
  
> [!NOTE]  
>  スクロールは、ODBC 2 でサポートされます。*x*によってドライバー **SQLExtendedFetch**です。 詳細については、次を参照してください。[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。
