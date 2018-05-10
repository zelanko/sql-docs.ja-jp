---
title: サーバーの全体管理で Power Pivot サイト用の信頼できる場所を作成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3dabb6a62434ce2956a0c11a62f3b383104df698
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-trusted-location-for-power-pivot-sites-in-central-administration"></a>サーバーの全体管理での Power Pivot サイト用の信頼できる場所の作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Excel Services では、SharePoint サーバーで開いたブックの有効なリポジトリの場所を指定できます。 これは「信頼できる場所」と呼ばれ、作成したそれぞれの信頼できる場所について異なる構成設定を使用できます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の配置の場合、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックが含まれるサイト用に信頼できる場所を作成し、ファームのその他の部分に対する既定値を保持しながら [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスに対しては最適な設定を適用できるようにすることを検討してください。  
  
  
## <a name="prerequisites"></a>前提条件  
 URL を信頼できる場所として指定するには、ファームまたはサービスの管理者である必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーか、ブックが保存されているその他のライブラリが含まれる SharePoint サイトの URL アドレスがわかっていることが必要です。 アドレスを取得するには、ライブラリがあるサイトを開き、 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー**を右クリックして、 **[プロパティ]** をクリックします。次に、サーバー名とサイト パスを含む [アドレス (URL)] の最初の部分をコピーします。  
  
##  <a name="overview"></a> 概要  
 Excel Services の最初のインストールでは、'http://' が信頼できる場所として指定されます。このため、ファームのどのサイトからアクセスしたブックもサーバーで開くことができます。 信頼できると見なされる場所の制御を厳しくする必要がある場合は、ファームの特定のサイトにマップする信頼できる場所を新しく作成し、各場所の設定とアクセス許可を変更します。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをホストするサイト用に新しい信頼できる場所を作成すると、ファームのその他の部分に対する既定値を保持しながら [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスに対しては最適な別の設定を適用する場合に特に便利です。 たとえば、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック用に最適化された信頼できる場所で最大ブック サイズを 50 MB にし、ファームの残りの部分で既定値の 10 MB を使用するように設定できます。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ライブラリを使用してパブリッシュ済みのブックをプレビューする場合に、予想したプレビュー イメージの代わりにデータ更新の警告が表示されるときは、信頼できる場所を作成することをお勧めします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーは、ドキュメント内のデータおよび表示情報を使用して、レポートとブックのサムネイル画像を表示します。 信頼できる場所で [データ更新に関する警告を表示する] が有効である場合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーに更新を実行するための十分な権限がなく、その結果、サムネイル画像の代わりにエラーが表示されることがあります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを新しい信頼できる場所として持つサイトを追加すると、この問題を解消できます。  
  
##  <a name="create"></a> Power Pivot データ アクセス用の信頼できる場所の作成  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  Excel Services サービス アプリケーションをクリックします。  
  
3.  **[信頼できるファイル保存場所]** をクリックします。  
  
4.  **[信頼できるファイル保存場所の追加]** をクリックします。  
  
5.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ライブラリがあるサイトの URL を入力します。  
  
6.  [場所の種類] で、 **[Microsoft SharePoint Foundation]** を選択します。  
  
    > [!IMPORTANT]  
    >  UNC と HTTP の場所の種類は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスではサポートされていません。  
  
7.  [セッションの管理]、[ブックのプロパティ]、および [計算動作] のプロパティの既定の設定をすべてそのまま使用します。  
  
8.  [ブックのプロパティ] で、 **[ブックの最大サイズ]** を「 **50**」に設定します。 これにより、ブックのファイル サイズの上限が、親 Web アプリケーションへのファイル アップロードの上限と同じになります。 ブックのサイズが 50 MB を超える場合は、ファイル サイズの上限をさらに増やす必要があります。 詳細については、「[アップロードするファイルの最大サイズの構成 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)」を参照してください。  
  
9. [外部データ] で、[外部データの許可] が **[信頼できるデータ接続ライブラリと、埋め込まれている接続]** に設定されていることを確認します。 この設定は、ブックでの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスに必要です。  
  
10. また、[外部データ] の [更新時の警告] で、 **[更新時の警告の有効化]** のチェック ボックスをオフにします。 このチェック ボックスをオフにすると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーで、定型の警告メッセージの代わりにブックのプレビュー イメージが表示されるようになります。  
  
11. **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Power Pivot ギャラリー](http://msdn.microsoft.com/library/2a0db616-e08e-4062-aac8-979f8cad7794)   
 [作成し、Power Pivot ギャラリーのカスタマイズ](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)   
 [Power Pivot ギャラリーを使用する](../../analysis-services/power-pivot-sharepoint/use-power-pivot-gallery.md)  
  
  
