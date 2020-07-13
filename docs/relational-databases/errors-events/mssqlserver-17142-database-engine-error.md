---
title: MSSQLSERVER_17142 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17142 (Database Engine error)
ms.assetid: 83a53507-ac76-4cb9-b116-daf6f42aea1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dd9f95d863c101b2b8bdc0d502fcafe5773d589f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780855"
---
# <a name="mssqlserver_17142"></a>MSSQLSERVER_17142
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|17142|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|INIT_SRVC_PAUSED|  
|メッセージ テキスト|SQL Server サービスが一時停止されました。 新しい接続は許可されません。 サービスを再開するには、SQL コンピューター マネージャーを使用するか、コントロール パネルの [サービス] を使用します。|  
  
## <a name="explanation"></a>説明  
サービス コントロール マネージャーによって SQL Server のサービスが一時停止されました。  
  
## <a name="user-action"></a>ユーザーの操作  
SQL Server 構成マネージャーを使用して SQL Server のサービスを再開します。  
  
