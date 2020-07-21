---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f83b574d6201d0845f23c9194ea2e873d90daa5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781484"
---
# <a name="mssqlserver_10520"></a>MSSQLSERVER_10520
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|10520|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_PARAM_NOT_ALLOWED|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。'%ls' として指定した @type のパラメーター '%ls' に NULL 以外の値を指定しています。 この型のパラメーターには、NULL 値を指定する必要があります。 パラメーターに NULL を指定するか、パラメーターに NULL 以外の値を指定可能な型に変更します。|  
  
## <a name="explanation"></a>説明  
@type で指定した型のパラメーターには、NULL 値を指定する必要がありますが、NULL 以外の値を指定しました。  
  
## <a name="user-action"></a>ユーザーの操作  
パラメーターに NULL を指定するか、パラメーターに NULL 以外の値を指定可能な型に変更します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
  
