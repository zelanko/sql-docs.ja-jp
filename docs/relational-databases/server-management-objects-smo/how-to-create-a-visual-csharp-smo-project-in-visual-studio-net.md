---
title: Visual Studio .NET で Visual c# SMO プロジェクトを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6645ab2f714b6d0e54299324a3406cc37319cc22
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Visual Studio .NET で Visual c# SMO プロジェクトを作成する方法
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。  
  
 この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。 インポート、**エージェント**名前空間は省略可能です。 使用するプログラムを作成しているときに使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントです。 **共通**名前空間がのインスタンスへのセキュリティで保護された接続を確立するために必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 **SqlClient** SQL 例外エラーを処理する名前空間を使用します。  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Visual studio.net で Visual c# SMO プロジェクトの作成  
  
1. Visual Studio を起動します。
  
2. **ファイル** メニューのをクリックして**新規**し**プロジェクト**です。  **[新しいプロジェクト]** ダイアログ ボックスが表示されます。   
  
3. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **インストール** ウィンドウに移動**テンプレート**\\**Visual c#**\\**Windows**選択と**コンソール アプリケーション**です。  
  
4. (省略可能)**名前**テキスト ボックスに、新しいアプリケーションの名前を入力します。  

5. をクリックして**OK**コンソール アプリケーション テンプレートを読み込めません。  

6. 上の指示に従って[SMO のインストール](installing-smo.md)を参照するプロジェクトのパッケージをインストールします。
  
7. **[表示]** メニューの **[コード]**をクリックします。
    
8. コードでは、名前空間ステートメントの前に、次の入力**を使用して**SMO 名前空間の型を修飾するためにステートメント。
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。 これらの名前空間は、必要に応じて追加します。  
  
16. SMO コードを追加できます。  
  
  
