---
title: Drivers | に直接接続するMicrosoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299082"
---
# <a name="connecting-directly-to-drivers"></a>ドライバーに直接接続する
このセクションで前述した「[データソースまたはドライバーの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」で説明したように、一部のアプリケーションでは、データソースをまったく使用したくありません。 代わりに、ドライバーに直接接続する必要があります。 **SQLDriverConnect**は、アプリケーションがデータソースを指定せずに直接ドライバーに接続する方法を提供します。 概念的には、一時データソースは実行時に作成されます。  
  
 ドライバーに直接接続するには、アプリケーションで、 **DSN**キーワードではなく、接続文字列に**driver**キーワードを指定します。 **Driver**キーワードの値は、 **sqldrivers**によって返されるドライバーの説明です。 たとえば、ドライバーに "Paradox ドライバー" という説明があり、データファイルが格納されているディレクトリの名前が必要であるとします。 このドライバーに接続するには、アプリケーションで次の接続文字列のいずれかを使用することがあります。  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 最初の文字列の場合、ドライバーは追加情報を必要としません。 2番目の文字列の場合、ドライバーは、データファイルが格納されているディレクトリの名前を要求する必要があります。
