---
title: "Integration Services サービスへのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSIS パッケージ, セキュリティ"
  - "実行中のパッケージの参照"
  - "実行中のパッケージの表示"
  - "セキュリティ [Integration Services], 実行中のパッケージ"
  - "パッケージ [Integration Services], セキュリティ"
  - "実行中の現在のパッケージ"
  - "Integration Services パッケージ, セキュリティ"
  - "SQL Server Integration Services パッケージ, セキュリティ"
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Integration Services サービスへのアクセス
  パッケージの保護レベルによって、パッケージを編集および実行できるユーザーを制限できます。 サーバーで現在実行中のパッケージの一覧を表示できるユーザー、および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で現在実行中のパッケージを停止できるユーザーを制限するには、追加の保護が必要です。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、実行中のパッケージを一覧表示する際に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが使用されます。 Windows の Administrators グループのメンバーは、実行中のすべてのパッケージを表示および停止できます。 Administrators グループのメンバーではないユーザーは、本人が起動したパッケージのみを表示および停止できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (特に、リモート フォルダーの列挙を行う可能性のある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス) を実行するコンピューターへのアクセスを制限することは重要です。 認証を受けたユーザーであれば、パッケージの列挙を要求できます。 サービスが見つからない場合でも、サービスはフォルダーを列挙します。 これらのフォルダー名が、悪意あるユーザーに悪用される場合があります。 管理者がリモート コンピューターのフォルダーを列挙できるようにサービスを設定した場合、ユーザーも通常は参照できないフォルダー名を参照することができます。  
  
  