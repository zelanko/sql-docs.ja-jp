---
title: IPD | の自動作成Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c1591843667ef01c6c88f5dfafb734f044679b2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67909830"
---
# <a name="automatic-population-of-the-ipd"></a>IPD の自動作成
一部のドライバーでは、パラメーター化クエリの準備が完了した後で、IPD のフィールドを設定できます。 記述子フィールドには、データ型、有効桁数、小数点以下桁数、およびその他の特性を含む、パラメーターに関する情報が自動的に設定されます。 これは、 **SQLDescribeParam**をサポートすることと同じです。 この情報は、アプリケーションが認識していないパラメーターを使用してアドホッククエリを実行する場合など、アプリケーションに対して他の探索方法がない場合に特に役立ちます。  
  
 アプリケーションは、SQL_ATTR_AUTO_IPD の*属性*を使用して**Sqlgetconnectattr**を呼び出すことによって、ドライバーが自動作成をサポートしているかどうかを判断します。 SQL_TRUE が返された場合、ドライバーはそれをサポートし、アプリケーションでは、SQL_ATTR_ENABLE_AUTO_IPD statement 属性を SQL_TRUE に設定することによって有効にすることができます。  
  
 自動作成がサポートされ、有効になっている場合、ドライバーは、パラメーターマーカーを含む SQL ステートメントが**SQLPrepare**を呼び出すことによって準備された後、IPD のフィールドを設定します。 アプリケーションでは、 **SQLGetDescField**または**Sqlgetdescrec**または**SQLDescribeParam**を呼び出すことによってこの情報を取得できます。 アプリケーションでは、この情報を使用して、パラメーターに最適なアプリケーションバッファーをバインドしたり、データ変換を指定したりすることができます。  
  
 IPD を自動で作成すると、パフォーマンスが低下する可能性があります。 アプリケーションでは、SQL_ATTR_ENABLE_AUTO_IPD ステートメントの属性を SQL_FALSE (既定値) にリセットすることによって、この設定をオフにすることができます。
