---
title: 部分クエリを実行する方法 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c6ed1362f7001a55b74538c165b373364b93df3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087474"
---
# <a name="how-to-execute-a-partial-query"></a>部分クエリを実行する方法
Transact\-SQL エディターでは、スクリプトの一部を選択し、その部分を単一のクエリとして実行することができます。 これにより、複雑なクエリをセクションに分けて、セクションごとに容易にデバッグできるようになります。  
  
> [!WARNING]  
> 以下に示す手順では、「[接続されているデータベース開発](../ssdt/connected-database-development.md)」および「[プロジェクト指向のオフライン データベース開発](../ssdt/project-oriented-offline-database-development.md)」に示されているこれまでの手順で作成したエンティティを使用します。  
  
### <a name="to-partially-execute-a-query"></a>クエリを部分的に実行するには  
  
1.  **SQL Server オブジェクト エクスプローラー**で、**[ビュー]** の下にある **PerishableFruits** をダブルクリックし、Transact\-SQL エディターで開きます。  
  
2.  コード内の「`SELECT p.Id, p.Name FROM dbo.Product p`」という部分を選択し、右クリックして、**[クエリの実行]** をクリックします。  
  
3.  `Products` テーブル内のすべての行の指定されたフィールドが、**結果**ペインに返されます。  
  
