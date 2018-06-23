---
title: Visual Studio .NET で Visual c# SMO プロジェクトを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b96b2f52b1d993c02536b70e39ba7d1868643a04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077489"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>Visual Studio .NET での Visual C# SMO プロジェクトの作成
  このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。  
  
 この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。 `Agent` 名前空間のインポートは省略可能です。 使用するプログラムを作成しているときに使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントです。 `Common` 名前空間は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのセキュリティで保護された接続を確立するために必要です。 `SqlClient` 名前空間は、SQL 例外エラーの処理を行うために使用されます。  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Visual studio.net で Visual c# SMO プロジェクトの作成  
  
1.  [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] または [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **プロジェクトの種類**ダイアログ ボックスで、 **Visual c#**、し、 **Windows**です。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]インストールされたテンプレート ペインで、 **Windows アプリケーション**です。  
  
4.  (省略可能)**名前**フィールドに、新しいアプリケーションの名前を入力  
  
5.  Visual C# アプリケーションの種類を選択します。 選択して、次の例の**コンソール アプリケーション**です。  
  
6.  **[プロジェクト]** メニューの **[参照の追加]** を選択します。 **[参照の追加]** ダイアログ ボックスが表示されます。  
  
7.  をクリックして**参照**で SMO アセンブリを探し、[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]フォルダー、および、次のファイルを選択します。 これらは、SMO アプリケーションのビルドに最低限必要なファイルです。  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  使用して、`Ctrl`キーを 1 つ以上のファイルを選択します。  
  
8.  必要に応じて任意の SMO アセンブリを追加します。 たとえば、[!INCLUDE[ssSB](../../includes/sssb-md.md)] に特化したプログラミングを行っている場合は、以下のアセンブリを追加します。  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. **[開く]** をクリックします。  
  
10. **ビュー**  メニューのをクリックして**コード**。 - または - Program1.cs [デザイン] ウィンドウを選択し、コード ウィンドウを表示する windows フォームをダブルクリックします。  
  
11. コードでは、名前空間ステートメントの前に、次の `using` ステートメントを入力し、SMO 名前空間の型を修飾します。  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。 これらの名前空間は、必要に応じて追加します。  
  
13. SMO コードを追加できます。  
  
  