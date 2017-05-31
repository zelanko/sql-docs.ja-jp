---
title: "マルチサーバー環境に適したエージェント サービス アカウントの選択 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 86d85a50ab48b48c25610def1d2d1816a5856255
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスに対して選択する Windows アカウントによって、マルチサーバー環境の動作に次のような影響が生じることがあります。  
  
-   ローカルの Windows Administrators グループのメンバーではないアカウントで [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを実行する場合、マスター サーバーへの対象サーバーの参加は、失敗する可能性があります。 その場合は、次のエラー メッセージが返されます。  
  
    "参加操作に失敗しました"  
  
    この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] サービスおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを再起動します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスがローカル システム アカウントで実行されるとき、マスター サーバーと対象サーバー間の操作は、同じコンピューターにマスター サーバーと対象サーバーの両方が存在する場合にのみサポートされます。 この構成を使用している場合に、対象サーバーをマスター サーバーに参加させると、次のメッセージが返されます。  
  
    "*<target_server_computer_name>* のエージェント開始アカウントに対象サーバーとしてのログオン権限があることを確認します"  
  
    情報提供を目的としたこのメッセージは無視できます。 参加操作は、正常に完了します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのアカウントの選択の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)」を参照してください。  
  

