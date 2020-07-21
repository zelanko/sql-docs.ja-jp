---
title: Visual Studio .NET で Visual Basic SMO プロジェクトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 49eb94833d10b2e901c008092aea29eab8e4ad48
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933683"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a>Visual Studio .NET での Visual Basic SMO プロジェクトの作成
  このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。  
  
 この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。 `Agent` 名前空間のインポートは省略可能です。 エージェントを使用するプログラムを作成するときに使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 `Common` 名前空間は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのセキュリティで保護された接続を確立するために必要です。 `SqlClient` 名前空間は、SQL 例外エラーの処理を行うために使用されます。  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a>Visual Studio .NET での Visual Basic SMO プロジェクトの作成  
  
1.  [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] または [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  [**プロジェクトの種類**] ダイアログボックスで、[ **Visual Basic**] を選択し、[ **Windows**] を選択します。 [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] インストールされたテンプレート] ペインで、[**コンソールアプリケーション**] を選択します。  
  
4.  Optional[**名前**] フィールドに、新しいアプリケーションの名前を入力します。  
  
5.  [ **OK** ] をクリックして、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コンソールアプリケーションテンプレートを読み込みます。  
  
6.  **[プロジェクト]** メニューの **[参照の追加]** を選択します。 **[参照の追加]** ダイアログ ボックスが表示されます。  
  
7.  [**参照**] をクリックし、C:\Program Server\120\SDK\Assemblies フォルダー内の SMO アセンブリを見つけて、次のファイルを選択します。 これらは、SMO アプリケーションのビルドに最低限必要なファイルです。  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc  
  
    > [!NOTE]  
    >  複数の `Ctrl` ファイルを選択するには、キーを使用します。  
  
8.  必要に応じて任意の SMO アセンブリを追加します。 たとえば、[!INCLUDE[ssSB](../../includes/sssb-md.md)] に特化したプログラミングを行っている場合は、以下のアセンブリを追加します。  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. **[開く]** をクリックします。  
  
10. [**表示**] メニューの [**コード**] をクリックするか、module1.vb ウィンドウを選択してコードウィンドウを表示します。  
  
11. コードでは、宣言の前に、次の**Imports**ステートメントを入力して、SMO 名前空間の型を修飾します。  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。 これらの名前空間は、必要に応じて追加します。  
  
13. SMO コードを追加できます。  
  
  
