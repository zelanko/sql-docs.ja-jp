---
title: 記述子 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca8299daae744fb9398ed6ffc99c838ce8edff48
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305903"
---
# <a name="descriptors"></a>記述子
記述子ハンドルは、列または動的パラメーターに関する情報を保持するデータ構造を参照します。  
  
 列およびパラメーター・データを操作する ODBC 関数は、記述子フィールドを暗黙的に設定および取得します。 たとえば、列データをバインドするために**SQLBindCol**が呼び出されると、バインディングを完全に記述する記述子フィールドが設定されます。 列データを記述するために**SQLColAttribute**が呼び出されると、記述子フィールドに格納されているデータが返されます。  
  
 ODBC 関数を呼び出すアプリケーションは、記述子に関係する必要はありません。 データベース操作では、アプリケーションが記述子に直接アクセスする必要はありません。 ただし、アプリケーションによっては、記述子に直接アクセスすると、多くの操作が合理化されます。 たとえば、記述子への直接アクセスは、**列**データを再バインドする方法を提供します。  
  
> [!NOTE]  
>  記述子の物理表現が定義されていません。 アプリケーションは、記述子ハンドルを使用して ODBC 関数を呼び出すことによって、そのフィールドを操作することによってのみ、記述子に直接アクセスできます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [記述子の種類](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [記述子フィールド](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [記述子の割り当てと解放](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [記述子フィールドの取得と設定](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
