---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d4f94fb3dccadaba54528d195c03c81ed1d9c63
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432411"
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
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
  
  
