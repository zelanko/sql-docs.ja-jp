---
title: MSSQLSERVER_10539 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5d54a85fe2f839e2339234b790acda4e1df0c549
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver10539"></a>MSSQLSERVER_10539
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10539|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NO_PLAN_FOR_STMT|  
|メッセージ テキスト|プラン ガイド '%.*ls' をキャッシュから作成できません。開始オフセット %d のステートメントのクエリ プランを使用できません。 この問題は、存在しないデータベース オブジェクトにステートメントが依存している場合に発生することがあります。 必要なデータベース オブジェクトがすべて存在することを確認し、プラン ガイドを作成する前にステートメントを実行します。|  
  
## <a name="explanation"></a>説明  
指定した開始オフセットを持つステートメントのクエリ プランがプラン キャッシュ内にありません。  
  
## <a name="user-action"></a>ユーザーの操作  
必要なデータベース オブジェクトがすべて存在することを確認し、プラン ガイドを作成する前にステートメントを実行します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

