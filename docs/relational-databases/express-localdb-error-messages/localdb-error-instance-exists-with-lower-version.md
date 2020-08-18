---
description: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5619878edb99204b3b55d99e2a538d662cfb1eb5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88409808"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a>LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>詳細  
  
| 属性 | 値 |
| --------- | ----- |
|製品名|SQL Server|  
|イベント ID|258|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|指定されたバージョンのローカル データベース インスタンスを作成できません。 同じ名前のインスタンスは既に存在しますが、指定されたバージョンよりも下位のバージョンになっています。|  
  
## <a name="explanation"></a>説明  
 指定したインスタンスは既に存在しますが、そのバージョンは要求よりも低いバージョンです。  
  
## <a name="user-action"></a>ユーザーの操作  
 既存のインスタンスを削除し、操作を再試行してください。  
  
  
