---
title: Integration Services サービスへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7dd6fbed4bedc285069306ab4c400f0f67f9f293
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439789"
---
# <a name="access-to-the-integration-services-service"></a>Integration Services サービスへのアクセス
  パッケージの保護レベルによって、パッケージを編集および実行できるユーザーを制限できます。 サーバーで現在実行中のパッケージの一覧を表示できるユーザー、および [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で現在実行中のパッケージを停止できるユーザーを制限するには、追加の保護が必要です。  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では、実行中のパッケージを一覧表示する際に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスが使用されます。 Windows の Administrators グループのメンバーは、実行中のすべてのパッケージを表示および停止できます。 Administrators グループのメンバーではないユーザーは、本人が起動したパッケージのみを表示および停止できます。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス (特に、リモート フォルダーの列挙を行う可能性のある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス) を実行するコンピューターへのアクセスを制限することは重要です。 認証を受けたユーザーであれば、パッケージの列挙を要求できます。 サービスが見つからない場合でも、サービスはフォルダーを列挙します。 これらのフォルダー名が、悪意あるユーザーに悪用される場合があります。 管理者がリモート コンピューターのフォルダーを列挙できるようにサービスを設定した場合、ユーザーも通常は参照できないフォルダー名を参照することができます。  
  
  
