---
title: Integration Services プロジェクトのインポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 020f81f5345fb59957a32364ce23199c9bf7f878
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084133"
---
# <a name="import-an-integration-services-project"></a>Integration Services プロジェクトのインポート
  既存の配置ファイル (.ispac) または Integration Services カタログに配置されたプロジェクトからプロジェクトを作成するには、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の**プロジェクトのインポート ウィザード**を使用します。 この機能は、プロジェクトの元のコピーがない状態で、.ispac ファイルまたは SSISDB カタログからプロジェクトを作成する場合に、特に便利です。  
  
### <a name="to-import-a-project"></a>プロジェクトをインポートするには  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]で、 **[ファイル]** > **メニューの** [新規作成] **[プロジェクト]** をクリックします。  
  
2.  **[新しいプロジェクト]** ウィンドウの **[インストールされているテンプレート]** 領域で **[ビジネス インテリジェンス]** を展開し、 **[Integration Services]** をクリックします。  
  
3.  プロジェクトの種類の一覧から **Integration Services プロジェクトのインポート ウィザード** をクリックします。  
  
4.  作成する新しいプロジェクトの名前を、 **[名前]** ボックスに入力します。  
  
5.  プロジェクトのパスまたは場所を **[場所]** ボックスに入力するか、または **[参照]** をクリックして選択します。  
  
6.  **[ソリューション名]** ボックスにソリューションの名前を入力します。  
  
7.  **[OK]** をクリックして **[Integration Services プロジェクトのインポート ウィザード]** ダイアログ ボックスを起動します。  
  
8.  **[次へ]** をクリックして、 **[ソースの選択]** ページに移動します。  
  
9. **.ispac** ファイルからインポートする場合は、ファイル名を含むパスを **[パス]** ボックスに入力します。 **[参照]** をクリックして、ソリューションを格納するフォルダーに移動し、 **[ファイル名]** ボックスにファイル名を入力して、 **[開く]** をクリックします。  
  
     **Integration Services カタログ**からインポートする場合は、データベース インスタンス名を **[サーバー名]** ボックスに入力するか、または **[参照]** をクリックしてカタログを含むデータベース インスタンスを選択します。  
  
     **[パス]** ボックスの横にある **[参照]** をクリックし、カタログのフォルダーを展開して、インポートするプロジェクトを選択し、 **[OK]** をクリックします。  
  
     **[次へ]** をクリックして **[確認]** ページに移動します。  
  
10. 情報を確認し、 **[インポート]** をクリックして、選択した既存のプロジェクトに基づくプロジェクトを作成します。  
  
11. 省略可能: **[レポートの保存]** をクリックして、結果をファイルに保存します  
  
12. **[閉じる]** をクリックして **[Integration Services プロジェクトのインポート ウィザード]** ダイアログ ボックスを閉じます。  
  
  