---
title: ドライバに直接接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6aacb5d3df985949e04cdd47a9fe460cddbde6a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299082"
---
# <a name="connecting-directly-to-drivers"></a>ドライバーに直接接続する
「[データ ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」で説明したように、このセクションでは、一部のアプリケーションではデータ ソースをまったく使用しません。 代わりに、ドライバーに直接接続する必要があります。 **SQLDriverConnect**は、データ ソースを指定せずに、アプリケーションがドライバーに直接接続するための方法を提供します。 概念的には、一時データ ソースは実行時に作成されます。  
  
 ドライバーに直接接続するには、アプリケーションは **、DSN**キーワードの代わりに、接続文字列で**DRIVER**キーワードを指定します。 **DRIVER**キーワードの値は **、SQLDrivers**によって返されるドライバーの説明です。 たとえば、ドライバーが ParadoxDriver という説明を持ち、データ ファイルを含むディレクトリの名前を必要とします。 このドライバに接続するには、アプリケーションで次のいずれかの接続文字列を使用する場合があります。  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 最初の文字列では、ドライバーは、任意の追加情報を必要としません。 2 番目の文字列では、ドライバーは、データ ファイルを含むディレクトリの名前を求める必要があります。
