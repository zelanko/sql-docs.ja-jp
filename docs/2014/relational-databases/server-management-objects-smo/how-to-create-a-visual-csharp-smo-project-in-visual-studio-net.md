---
title: Visual Studio .NET で Visual C# SMO プロジェクトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfc8e5cf35a7f03f485bc3ff9e94ee70eab2cea2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997076"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>Visual Studio .NET での Visual C# SMO プロジェクトの作成
  このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。  
  
 この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。 `Agent` 名前空間のインポートは省略可能です。 エージェントを使用するプログラムを作成するときに使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 `Common` 名前空間は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのセキュリティで保護された接続を確立するために必要です。 `SqlClient` 名前空間は、SQL 例外エラーの処理を行うために使用されます。  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Visual C# SMO プロジェクトを Visual Studio.NET で作成する  
  
1.  [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] または [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  [**プロジェクトの種類**] ダイアログボックスで、[ **Visual C#**] を選択し、[ **Windows**] を選択します。 [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] インストールされたテンプレート] ペインで、[ **Windows アプリケーション**] を選択します。  
  
4.  Optional[**名前**] フィールドに、新しいアプリケーションの名前を入力します。  
  
5.  Visual C# アプリケーションの種類を選択します。 次の例では、[**コンソールアプリケーション**] を選択します。  
  
6.  **[プロジェクト]** メニューの **[参照の追加]** を選択します。 **[参照の追加]** ダイアログ ボックスが表示されます。  
  
7.  [**参照**] をクリックし、フォルダー内の SMO アセンブリを見つけ [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] て、次のファイルを選択します。 これらは、SMO アプリケーションのビルドに最低限必要なファイルです。  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  複数の `Ctrl` ファイルを選択するには、キーを使用します。  
  
8.  必要に応じて任意の SMO アセンブリを追加します。 たとえば、[!INCLUDE[ssSB](../../includes/sssb-md.md)] に特化したプログラミングを行っている場合は、以下のアセンブリを追加します。  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. **[開く]** をクリックします。  
  
10. [**表示**] メニューの [**コード**] をクリックします。または、[Program1.cs [Design]] ウィンドウを選択し、windows フォームをダブルクリックしてコードウィンドウを表示します。  
  
11. コードでは、名前空間ステートメントの前に、次の `using` ステートメントを入力し、SMO 名前空間の型を修飾します。  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。 これらの名前空間は、必要に応じて追加します。  
  
13. SMO コードを追加できます。  
  
  
