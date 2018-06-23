---
title: '手順 1: 新しい Integration Services プロジェクトの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3237d8a39b1d53b60fca2fcd65da0619d74a6300
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164338"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>手順 1: 新しい Integration Services プロジェクトの作成
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でパッケージを作成するには、まず [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成する必要があります。 このプロジェクトには、データ変換ソリューションで使用するオブジェクト (データ ソース、データ ソース ビュー、パッケージ) のテンプレートが用意されています。  
  
 この [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] チュートリアルで作成するパッケージは、ロケール依存型データの値を解釈します。 コンピューターが地域オプション [英語 (米国)] を使用するように構成されていない場合は、パッケージ内で追加のプロパティを設定する必要があります。 レッスン 2 から 5 では、レッスン 1 で作成したパッケージをコピーして使用します。コピーしたパッケージでは、ロケール依存型のプロパティを更新する必要はありません。  
  
> [!NOTE]  
>  このチュートリアルには、Microsoft SQL Server Data Tools が必要です。  
>   
>  SQL Server Data Tools のインストールの詳細については、「[SQL Server Data Tools のダウンロード](http://msdn.microsoft.com/data/hh297027)」を参照してください。  
  
### <a name="to-create-a-new-integration-services-project"></a>新しい Integration Services プロジェクトを作成するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]**、 **[Microsoft SQL Server]** の順にポイントし、 **[SQL Server Data Tools]** をクリックします。  
  
2.  新しい **プロジェクトを作成するため、** [ファイル] **メニューの**[新規作成] **をポイントし、** [プロジェクト] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] をクリックします。  
  
3.  **[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]** を展開し、 **[テンプレート]** ペインで **[Integration Services プロジェクト]** を選択します。  
  
4.  **[名前]** ボックスに表示されている既定の名前を「 **SSIS Tutorial**」に変更します。 必要に応じて、 **[ソリューションのディレクトリを作成]** チェック ボックスをオフにします。  
  
5.  既定の場所をそのまま使用するか、 **[参照]** をクリックして使用するフォルダーを指定します。 **[プロジェクトの場所]** ダイアログ ボックスで、目的のフォルダーをクリックして **[フォルダーの選択]** をクリックします。  
  
6.  **[OK]** をクリックします。  
  
     既定では、 **Package.dtsx**という名前の空のパッケージが作成され、SSIS パッケージの下のプロジェクトに追加されます。  
  
7.  **ソリューション エクスプローラー** で **[Package.dtsx]** を右クリックし、 **[名前の変更]** をクリックします。表示されている既定のパッケージ名を「 **Lesson 1.dtsx**」に変更します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 2: フラット ファイル接続マネージャーの追加と構成](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  