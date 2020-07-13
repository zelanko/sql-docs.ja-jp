---
title: モジュールと Prologs (XQuery) |Microsoft Docs
description: XQuery プロローグで名前空間を宣言するときにサポートされない仕様について説明します。
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
ms.openlocfilehash: c7d982e8c944ff1c596dfa4178ce613ec3be709e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759498"
---
# <a name="modules-and-prologs-xquery"></a>モジュールとプロローグ (XQuery)
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)は一連の名前空間宣言です。 プロローグで名前空間の宣言を使用すると、名前空間のバインドにプレフィックスを指定して、クエリ本文でそのプレフィックスを使用できます。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 次の XQuery 仕様は、この実装ではサポートされていません。  
  
-   モジュール宣言 ( `version` )  
  
-   モジュール宣言 ( `module namespace` )  
  
-   Xmpspacedeclaration ( `xmlspace` )  
  
-   既定の照合順序の宣言 (`declare default collation`)  
  
-   ベース URI 宣言 ( `declare base-uri` )  
  
-   構築宣言 (`declare construction`)  
  
-   既定の順序の宣言 (`declare ordering`)  
  
-   スキーマのインポート (`import schema namespace`)  
  
-   モジュールのインポート ( `import module` )  
  
-   プロローグでの変数宣言 (`declare variable`)  
  
-   関数宣言 (`declare function`)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)  
 XQuery プロローグについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
