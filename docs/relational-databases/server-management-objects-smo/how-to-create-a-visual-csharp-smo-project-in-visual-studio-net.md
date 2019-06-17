---
title: Visual Studio .NET で Visual c# SMO プロジェクトの作成 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2bc775f7f857bffb5a7840d99de00fc546e71d03
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62943028"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Visual Studio .NET で Visual C# SMO プロジェクトを作成する方法
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。  
  
 この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。 インポート、**エージェント**名前空間は省略可能です。 使用するプログラムを記述するときに使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。 **共通**名前空間がのインスタンスへのセキュリティで保護された接続を確立するために必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 **SqlClient**名前空間は、SQL 例外エラーの処理に使用されます。  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Visual studio.net で Visual c# SMO プロジェクトを作成します。  
  
1. Visual Studio の起動
  
2. **ファイル** メニューのをクリックして**新規**し**プロジェクト**します。  **[新しいプロジェクト]** ダイアログ ボックスが表示されます。   
  
3. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **インストール済み**ウィンドウに移動します**テンプレート**\\**Visual c#** \\**Windows**選択と**コンソール アプリケーション**します。  
  
4. (省略可能)**名前**テキスト ボックスに、新しいアプリケーションの名前を入力します。  

5. をクリックして**OK**コンソール アプリケーション テンプレートを読み込めません。  

6. 指示に従って、 [SMO のインストール](installing-smo.md)を参照するプロジェクトのパッケージをインストールします。
  
7. **[表示]** メニューの **[コード]** をクリックします。
    
8. 名前空間のステートメントの前に、のコードで、次の入力**を使用して**SMO 名前空間の型を修飾するステートメント。
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。 これらの名前空間は、必要に応じて追加します。  
  
16. SMO コードを追加できます。  
  
  
