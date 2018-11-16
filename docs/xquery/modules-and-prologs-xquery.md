---
title: モジュールとプロローグ (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cc8c582f4a4e984bd203071f5ce59f986765e840
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291518"
---
# <a name="modules-and-prologs-xquery"></a>モジュールとプロローグ (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)一連の名前空間の宣言です。 プロローグで名前空間の宣言を使用すると、名前空間のバインドにプレフィックスを指定して、クエリ本文でそのプレフィックスを使用できます。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 次の XQuery 仕様は、この実装ではサポートされません。  
  
-   モジュール宣言 (`version`)  
  
-   モジュール宣言 (`module namespace`)  
  
-   Xmpspacedeclaration (`xmlspace`)  
  
-   既定の照合順序の宣言 (`declare default collation`)  
  
-   基本 URI 宣言 (`declare base-uri`)  
  
-   構築宣言 (`declare construction`)  
  
-   既定の順序の宣言 (`declare ordering`)  
  
-   スキーマのインポート (`import schema namespace`)  
  
-   モジュールのインポート (`import module`)  
  
-   プロローグでの変数宣言 (`declare variable`)  
  
-   関数宣言 (`declare function`)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)  
 XQuery プロローグをについて説明します。  
  
## <a name="see-also"></a>参照  
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
