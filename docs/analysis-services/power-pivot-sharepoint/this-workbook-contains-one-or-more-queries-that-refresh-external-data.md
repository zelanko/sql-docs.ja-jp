---
title: このブックに外部データを更新する 1 つまたは複数のクエリが含まれています |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61056ecc8b49e7d21cd15702116da511a517ef31
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>このブックには、外部データを更新する 1 つまたは複数のクエリが含まれています。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれる Excel ブックの場合、Excel Services は接続情報が検出されるとこの警告を表示し、このブックのクエリを有効にするか無効にするかを確認するプロンプトを表示します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint|  
|[製品バージョン]|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|原因|Excel Services がデータ更新時に警告を表示するように構成されています。|  
|メッセージ テキスト|このブックには外部データを更新する 1 つ以上のクエリが含まれています。 悪意のあるユーザーは資格情報にアクセスし、他のユーザーに配布したり、他の有害なアクションを実行するようにクエリを書き換えることがあります。<br /><br /> このブックのソースを信頼できる場合は、[はい] をクリックしてこのブックの外部データに対するクエリを有効にします。 信頼できるかどうかが不明である場合は、[いいえ] をクリックして変更がブックに適用されないようにします。<br /><br /> このブックの外部データへのクエリを有効にしますか?|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックに、データの読み込みと計算を行う外部 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サーバーと通信する Excel で使用される埋め込みデータ接続文字列が含まれています。 [データ更新に関する警告を表示する] が有効になっている場合、Excel Services はこの接続文字列を検出し、ユーザーにその旨を警告します。  
  
 ブックの [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データをフィルターおよびスライスする場合は、クエリを有効にする必要があります。 信頼できる [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックのクエリのみを有効にしてください。  
  
## <a name="user-action"></a>ユーザーの操作  
 **[はい]** をクリックしてクエリを有効にします。  
  
 また、構成設定を変更して、更新時に警告が表示されないようにすることもできます。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  **[Excel Services アプリケーション]** をクリックします。  
  
3.  **[信頼できるファイル保存場所]** をクリックします。  
  
4.  **[http://]** または構成する場所をクリックします。  
  
5.  [外部データ] で、 **[データ更新に関する警告を表示する]** チェック ボックスをオフにします。  
  
6.  **[OK]** をクリックします。  
  
 または、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックが含まれるサイト用に新しく信頼できる場所を作成し、そのサイトの構成設定だけを変更することもできます。 詳細については、「 [サーバーの全体管理での Power Pivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
  
