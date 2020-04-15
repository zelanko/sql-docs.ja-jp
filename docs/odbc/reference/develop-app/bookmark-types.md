---
title: ブックマークの種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 26d0297cd9dc57e9f30945a9248b235ae469da3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306333"
---
# <a name="bookmark-types"></a>ブックマークの種類
ODBC *3.x*のすべてのブックマークは可変長のブックマークです。 これにより、テーブルに関連付けられた主キーまたは一意のインデックスをブックマークとして使用できます。 また、ODBC *2.x*で使用されていたように、ブックマークは 32 ビット値にすることもできます。 ブックマークをカーソルと共に使用するように指定するには、ODBC *3.x*アプリケーションは SQL_ATTR_USE_BOOKMARK ステートメント属性を SQL_UB_VARIABLE に設定します。 可変長ブックマークが自動的に使用されます。  
  
 アプリケーションは、引数*FieldIdentifier*を SQL_DESC_OCTET_LENGTH に設定して**SQLColAttribute**を呼び出して、ブックマークの長さを取得できます。 可変長ブックマークは長い値になる可能性があるため、行セット内の行の多くについてブックマークを使用しない限り、アプリケーションは列 0 にバインドしないでください。  
  
 固定長ブックマークは、下位互換性を保つためにのみサポートされます。 ODBC *3.x*ドライバーを使用して動作する ODBC *2.x*アプリケーションが**SQLSetStmtOption**を呼び出してSQL_USE_BOOKMARKSをSQL_UB_ONに設定すると、ドライバー マネージャーでSQL_UB_VARIABLEにマップされます。 可変長ブックマークは、32 ビットしか設定されていない場合でも使用されます。 ドライバーは固定長のブックマークをサポートしている場合、可変長ブックマークをサポートします。 ODBC *2.x*ドライバーを使用して動作する ODBC *3.x*アプリケーションが**sqlSetStmtAttr**を呼び出してSQL_ATTR_USE_BOOKMARKSを SQL_UB_VARIABLE に設定すると、ドライバー マネージャーで SQL_UB_ON にマップされ、32 ビット固定長ブックマークが使用されます。 SQL_ATTR_FETCH_BOOKMARK_PTRステートメント属性は、32 ビットのブックマークを指す必要があります。 使用するブックマークが 32 ビットより長い場合 (主キーがブックマークとして使用される場合など)、カーソルは実際の値を 32 ビット値にマップする必要があります。 たとえば、それらのハッシュ テーブルを作成できます。 ODBC *2.x*ドライバを使用する ODBC *3.x*アプリケーションがブックマークをバインドする場合、バッファの長さは 4 でなければなりません。
