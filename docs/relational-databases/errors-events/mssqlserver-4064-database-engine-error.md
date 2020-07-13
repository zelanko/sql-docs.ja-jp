---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 711f182407fa3b06c48fd81d36dcf80558adaf90
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717862"
---
# <a name="mssqlserver_4064"></a>MSSQLSERVER_4064
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|4064|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DB_UFAIL_FATAL|  
|メッセージ テキスト|ユーザーの既定データベースを開けません。 ログインできませんでした。|  
  
## <a name="explanation"></a>説明  
SQL Server ログインの既定のデータベースに問題があるため接続できませんでした。 データベース自体が無効であるか、ログインにデータベースでの CONNECT 権限がありません。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER LOGIN を使用して、ログインの既定のデータベースを変更します。 CONNECT 権限をログインに許可します。  
  
