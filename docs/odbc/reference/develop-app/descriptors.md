---
title: 記述子 |Microsoft ドキュメント
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
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8362a8dd210579ebca0d303ca29661a3774ea4cd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="descriptors"></a>記述子
記述子ハンドルは、列または動的パラメーターのいずれかに関する情報を保持するデータ構造体を指します。  
  
 暗黙的に列やパラメーターのデータを操作する ODBC 関数を設定および記述子フィールドを取得します。 インスタンスのときに、 **SQLBindCol**が呼び出された列のデータをバインドするバインディングを完全に記述する記述子フィールドを設定します。 ときに**SQLColAttribute**が呼び出された列のデータを記述する記述子フィールドに格納されたデータを返します。  
  
 ODBC 関数を呼び出すアプリケーションでは、記述子を考慮が必要です。 アプリケーションにアクセスするダイレクト記述子データベース操作は不要です。 ただし、一部のアプリケーションでは、多くの操作を合理化記述子に直接アクセスできます。 たとえば、列のデータは、呼び出し元よりも効率的にすることができますを再バインドする方法を提供する記述子へのアクセスを指示**SQLBindCol**もう一度です。  
  
> [!NOTE]  
>  記述子の物理的に表したものが定義されていません。 アプリケーションは、記述子ハンドルを使用して ODBC 関数を呼び出すことによって、フィールドを操作することによってのみ、記述子への直接アクセスを利用できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [記述子の種類](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [記述子フィールド](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [記述子の割り当てと解放](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [記述子フィールドの取得と設定](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
