---
title: カタログ関数から返されるデータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], result sets
- functions [ODBC], catalog functions
ms.assetid: 399e1a64-8766-4c44-81ff-445399b7a1de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0d9b63de04f79fd95c1b06d8e84d85c6f4fea02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305232"
---
# <a name="data-returned-by-catalog-functions"></a>カタログ関数によって返されるデータ
各カタログ関数は、結果セットとしてデータを返します。 この結果セットは、他の結果セットと変わりません。 通常、ドライバーでハードコーディングされた、またはデータ ソースのプロシージャに格納されている、定義済みのパラメーター化された**SELECT**ステートメントによって生成されます。 結果セットからデータを取得する方法については、「[結果セットが作成されましたか?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
 各カタログ関数の結果セットは、その関数の参照項目に記述されています。 一覧の列に加えて、結果セットには、最後の定義済みの列の後にドライバー固有の列を含めることができます。 これらの列 (存在する場合) については、ドライバーのドキュメントで説明します。  
  
 アプリケーションは、結果セットの末尾に関連するドライバー固有の列をバインドする必要があります。 つまり、ドライバー固有の列の数を最後の列の数として計算する必要があります ( **SQLNumResultCols**で取得 ) 必要な列の後に発生する列の数を減らします。 これにより、新しい列が ODBC またはドライバーの将来のバージョンで結果セットに追加されたときに、アプリケーションを変更する必要が省けます。 このスキームが機能するためには、ドライバーは、結果セットの末尾に対して列番号が変更しないように、古いドライバー固有の列の前に新しいドライバー固有の列を追加する必要があります。  
  
 結果セットに返される識別子は、特殊文字が含まれている場合でも、引用符で囲まれません。 たとえば、識別子の引用文字 (ドライバー固有で**SQLGetInfo**を通じて返される) が二重引用符 (") で、買掛金勘定テーブルに顧客名という名前の列が含まれているとします。 この列の**SQLColumns**によって返される行では、TABLE_NAME列の値は買掛金勘定ではなく「買掛金」であり、COLUMN_NAME列の値は「顧客名」ではなく顧客名です。 買掛金勘定テーブルの顧客の名前を取得するには、アプリケーションは、これらの名前を引用します。  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 詳細については、「[引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)」を参照してください。  
  
 カタログ関数は、ユーザー名とパスワードに基づいて接続が行われ、ユーザーが特権を持つデータのみが返される SQL のような許可モデルに基づいています。 このモデルに適合しない個々のファイルのパスワード保護は、ドライバで定義されます。  
  
 カタログ関数によって返される結果セットはほとんど更新不可能であり、アプリケーションはこれらの結果セットのデータを変更することによってデータベースの構造を変更できるとは考えるべきではありません。
