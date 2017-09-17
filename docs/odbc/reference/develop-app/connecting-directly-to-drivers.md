---
title: "ドライバーに直接接続する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bacb659cb6986f86151502998523ade468f7cedd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-directly-to-drivers"></a>ドライバーに直接接続します。
説明したよう[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)、このセクションで前述した一部のアプリケーションがデータ ソースをまったく使用しないようにします。 代わりに、ドライバーに直接接続します。 **SQLDriverConnect**アプリケーションがデータ ソースを指定せずに、ドライバーに直接接続する方法を提供します。 概念的には、一時的なデータ ソースは実行時に作成されます。  
  
 ドライバーに直接接続する場合、アプリケーションを指定します、**ドライバー**の代わりに、接続文字列キーワードで、 **DSN**キーワード。 値、**ドライバー**キーワードは、によって返されるように、ドライバーの説明を**SQLDrivers**です。 たとえば、ドライバーは Paradox ドライバーの説明があるため、データ ファイルを含むディレクトリの名前が必要です。 このドライバーに接続するには、アプリケーションは次の接続文字列のいずれかで使用可能性があります。  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 最初の文字列で、ドライバーはその他の情報を必要はありません。 2 番目の文字列で、ドライバーは、データ ファイルを含むディレクトリの名前を要求する必要があります。
