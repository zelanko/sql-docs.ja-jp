---
title: 方法:部分クエリを実行する | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0dff2087286035b078f59ac1673a733fb3cc8358
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65090172"
---
# <a name="how-to-execute-a-partial-query"></a>方法:部分クエリを実行する
Transact\-SQL エディターでは、スクリプトの一部を選択し、その部分を単一のクエリとして実行することができます。 これにより、複雑なクエリをセクションに分けて、セクションごとに容易にデバッグできるようになります。  
  
> [!WARNING]  
> 以下に示す手順では、「[接続されているデータベース開発](../ssdt/connected-database-development.md)」および「[プロジェクト指向のオフライン データベース開発](../ssdt/project-oriented-offline-database-development.md)」に示されているこれまでの手順で作成したエンティティを使用します。  
  
### <a name="to-partially-execute-a-query"></a>クエリを部分的に実行するには  
  
1.  **SQL Server オブジェクト エクスプローラー**で、**[ビュー]** の下にある **PerishableFruits** をダブルクリックし、Transact\-SQL エディターで開きます。  
  
2.  コード内の「`SELECT p.Id, p.Name FROM dbo.Product p`」という部分を選択し、右クリックして、**[クエリの実行]** をクリックします。  
  
3.  `Products` テーブル内のすべての行の指定されたフィールドが、**結果**ペインに返されます。  
  
