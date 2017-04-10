---
title: "子パッケージの実装 | Microsoft Docs"
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
  - "子パッケージ"
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# 子パッケージの実装
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を使用して負荷分散を実装すると、子パッケージが他のサーバーにインストールされ、利用可能な CPU 時間またはサーバー時間を活用することができます。 子パッケージを作成および実行するには、次の手順を実行します。  
  
-   子パッケージをデザインします。  
  
-   パッケージをリモート サーバーに移動します。  
  
-   子パッケージを実行するステップを含む SQL Server エージェント ジョブをリモート サーバー上に作成します。  
  
-   SQL Server エージェント ジョブと子パッケージをテストおよびデバッグします。  
  
 子パッケージをデザインする際、子パッケージにはデザイン上の制限がないため、目的の機能をすべて追加できます。 ただし、パッケージからデータにアクセスする場合は、パッケージを実行するサーバーからそのデータにアクセスできなければなりません。  
  
 子パッケージを実行する親パッケージを識別するには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーでパッケージを右クリックし、**[エントリ ポイント パッケージ]** をクリックします。  
  
 子パッケージをデザインしたら、次に、そのパッケージをリモート サーバーに配置します。  
  
## リモート インスタンスへの子パッケージの移動  
 パッケージを他のサーバーに移動する方法は何種類かあります。 次の 2 つの方法をお勧めします。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してパッケージをエクスポートします。  
  
-   パッケージを配置します。パッケージを配置するには、配置するパッケージを含むプロジェクトの配置ユーティリティをビルドした後、パッケージ インストール ウィザードを実行し、パッケージをファイル システムまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにインストールします。 詳細については、「[レガシー パッケージの配置 &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)」を参照してください。  
  
 この配置は、使用する各リモート サーバーに対してそれぞれ行う必要があります。  
  
## SQL Server エージェント ジョブの作成  
 子パッケージをさまざまなサーバーに配置した後、子パッケージを格納した各サーバー上に SQL Server エージェント ジョブを作成します。 SQL Server エージェント ジョブには、ジョブ エージェントの呼び出し時に子パッケージを実行するステップが含まれています。 SQL Server エージェント ジョブは定期ジョブではありません。つまり、子パッケージは、親パッケージによって呼び出されたときだけ実行されます。 ジョブの成功や失敗に関する親パッケージへの通知は、SQL Server エージェント ジョブの成功や失敗、およびそのジョブが正常に呼び出されたかどうかを表すものであり、子パッケージが実行されたかどうかや、その成功や失敗については反映されません。  
  
## SQL Server エージェント ジョブと子パッケージのデバッグ  
 次のいずれかの方法を使用して、SQL Server エージェント ジョブとその子パッケージをテストできます。  
  
-   **[デバッグ]** メニューの **[デバッグなしで開始]** をクリックして、SSIS デザイナーで各子パッケージを実行します。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してリモート コンピューター上の個別の SQL Server エージェント ジョブを実行し、パッケージが実行されていることを確認します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブから実行するパッケージのトラブルシューティング方法については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報の「[SQL Server エージェントのジョブ ステップから SSIS パッケージを呼び出したときに SSIS パッケージが実行されない](http://support.microsoft.com/kb/918760)」を参照してください。  
  
 SQL Server エージェントは、ジョブ ステップを実行するたびに、プロキシに対してサブシステムのアクセス許可を確認し、プロキシへのアクセスを確立します。  
  
 プロキシは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で作成できます。  
  
## 関連タスク  
  
-   [SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  