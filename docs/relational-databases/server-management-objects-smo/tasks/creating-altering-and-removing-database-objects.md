---
title: データベース オブジェクトの使用 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c79ccb4805030cb93e67fa335e72de4d5984a62a
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583574"
---
# <a name="creating-altering-and-removing-database-objects"></a>データベース オブジェクトの作成、変更、および削除
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO オブジェクトの作成には次の段階があります。  
  
1.  オブジェクトのインスタンスの作成。  
  
2.  オブジェクト プロパティの設定。  
  
3.  子オブジェクトのインスタンスの作成。  
  
4.  子オブジェクト プロパティの設定。  
  
5.  オブジェクトの作成。  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 SMO アプリケーションで SMO オブジェクトのインスタンスを作成するときのインスタンスに存在しない[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]まで、**作成**メソッドが発行されます。 ただし、発行する必要はありません、**作成**個々 のオブジェクトに対してメソッド。 親オブジェクトのみが実行に必要なオブジェクトに子オブジェクトのセットがある場合、**作成**メソッド。 たとえば、テーブルの定義には、テーブルに含まれている列が 1 つ以上必要になります。 一方、テーブルがなくては列が独立して存在することはできません。 テーブルとテーブルの列の間には共存関係があります。  
  
 <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> メソッドを使用すると、オブジェクトへの変更を行うことができます。 オブジェクト コレクションの 1 つへの子オブジェクトの追加や、プロパティ値の変更など、1 つのオブジェクトに対する複数の変更は、バッチ化されて 1 つの変更として実行されます。 **Alter**メソッドは、ネットワーク トラフィックが減少し、全体的なパフォーマンスが向上します。  
  
 **ドロップ**ステートメントを使用してオブジェクトおよびオブジェクトを最初に作成するために必要なすべての共存子オブジェクトを削除します。  
  
## <a name="see-also"></a>参照  
 [SMO オブジェクト モデル](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
