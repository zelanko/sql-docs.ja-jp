---
title: "信頼できる場所が外部データ接続を許可されていません |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dc0cedfd-a7d0-40ef-bdd6-ea508130640a
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f774f6bc9a4d950d8f7c00e3c3e79aa3211e4cf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="trusted-location-does-not-allow-external-data-connections"></a>信頼できる場所が外部データ接続を許可しません。
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含む Excel ブックで、Excel Services は、埋め込みデータ ソースに接続できない場合にこのエラーを返します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|外部データ アクセスを拒否するように Excel Services が構成されています。|  
|メッセージ テキスト|ブックが保存されている信頼できる場所で、外部データ接続が許可されていません。 以下の接続を更新できませんでした: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックには、埋め込みデータ接続が含まれています。 スライサーやフィルターを介したブックの操作をサポートするには、埋め込まれている接続情報を使用した外部データ アクセスを許可するように Excel Services を構成する必要があります。 外部データ アクセスは、ファームの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーに読み込まれる [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを取得するのに必要です。  
  
## <a name="user-action"></a>ユーザーの操作  
 埋め込みデータ ソースを許可するように構成設定を変更します。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]**をクリックします。  
  
2.  **[Excel Services アプリケーション]**をクリックします。  
  
3.  **[信頼できるファイル保存場所]**をクリックします。  
  
4.  **[http://]** または構成する場所をクリックします。  
  
5.  [外部データ] の [外部データの許可] で、 **[信頼できるデータ接続ライブラリと、埋め込まれている接続]**をクリックします。  
  
6.  **[OK]**をクリックします。  
  
 または、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックが含まれるサイト用に新しく信頼できる場所を作成し、そのサイトの構成設定だけを変更することもできます。 詳細については、「 [サーバーの全体管理での Power Pivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
  

