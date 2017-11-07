---
title: "このブックに外部データを更新する 1 つまたは複数のクエリが含まれています |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f400a5513fcd16ea5344157e451d06b8fe103796
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>このブックには、外部データを更新する 1 つまたは複数のクエリが含まれています。
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれる Excel ブックの場合、Excel Services は接続情報が検出されるとこの警告を表示し、このブックのクエリを有効にするか無効にするかを確認するプロンプトを表示します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|原因|Excel Services がデータ更新時に警告を表示するように構成されています。|  
|メッセージ テキスト|このブックには外部データを更新する 1 つ以上のクエリが含まれています。 悪意のあるユーザーは資格情報にアクセスし、他のユーザーに配布したり、他の有害なアクションを実行するようにクエリを書き換えることがあります。<br /><br /> このブックのソースを信頼できる場合は、[はい] をクリックしてこのブックの外部データに対するクエリを有効にします。 信頼できるかどうかが不明である場合は、[いいえ] をクリックして変更がブックに適用されないようにします。<br /><br /> このブックの外部データへのクエリを有効にしますか?|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックに、データの読み込みと計算を行う外部 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サーバーと通信する Excel で使用される埋め込みデータ接続文字列が含まれています。 [データ更新に関する警告を表示する] が有効になっている場合、Excel Services はこの接続文字列を検出し、ユーザーにその旨を警告します。  
  
 ブックの [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データをフィルターおよびスライスする場合は、クエリを有効にする必要があります。 信頼できる [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックのクエリのみを有効にしてください。  
  
## <a name="user-action"></a>ユーザーの操作  
 **[はい]** をクリックしてクエリを有効にします。  
  
 また、構成設定を変更して、更新時に警告が表示されないようにすることもできます。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]**をクリックします。  
  
2.  **[Excel Services アプリケーション]**をクリックします。  
  
3.  **[信頼できるファイル保存場所]**をクリックします。  
  
4.  **[http://]** または構成する場所をクリックします。  
  
5.  [外部データ] で、 **[データ更新に関する警告を表示する]**チェック ボックスをオフにします。  
  
6.  **[OK]**をクリックします。  
  
 または、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックが含まれるサイト用に新しく信頼できる場所を作成し、そのサイトの構成設定だけを変更することもできます。 詳細については、「 [サーバーの全体管理での Power Pivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
  

