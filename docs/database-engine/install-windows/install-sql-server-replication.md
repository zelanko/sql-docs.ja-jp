---
title: "SQL Server レプリケーションのインストール | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンポーネント [SQL Server レプリケーション]"
  - "コマンド ラインからのインストール [SQL Server レプリケーション]"
  - "レプリケーションのインストール"
  - "レプリケーション [SQL Server]、インストール"
  - "コマンド ライン プロンプト [SQL Server レプリケーション]"
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
caps.latest.revision: 41
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 41
---
# SQL Server レプリケーションのインストール
  レプリケーション コンポーネントのインストールは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプトを使用して行うことができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールする場合、または既存のインスタンスを変更する場合はレプリケーションをインストールします。  
  
 レプリケーション コンポーネントのインストール後、レプリケーションを使用する前にサーバーを構成する必要があります。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)」を参照してください。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既存のインスタンスを変更するときにレプリケーション コンポーネントをインストールする場合は、インストール完了後に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止して再起動する必要があります。 この操作により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがレプリケーション エージェント サブシステムを認識し、ジョブ ステップからレプリケーション エージェントを呼び出すことができるようになります。  
  
## セットアップ プログラムによるレプリケーションのインストール  
 **の新しいインスタンスをインストールするときにレプリケーションをインストールするには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   レプリケーション管理オブジェクト (RMO) を含めてレプリケーション コンポーネントをインストールするには、インストール ウィザードの **[機能の選択]** ページで **[SQL Server レプリケーション]** を選択します。  
  
## コマンド プロンプトによるレプリケーションのインストール  
 **の新しいインスタンスをインストールするときにレプリケーションをインストールするには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   「[コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。  
  
## 参照  
 [SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016.md)   
 [コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [SQL Server 2016 の各エディションでサポートされる機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
  