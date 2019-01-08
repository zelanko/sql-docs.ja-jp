---
title: 接続を確立の試行中にエラーが発生しました |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28d5bd077da96e3dd6f8a48004c3a5df1b681f61
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215747"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection"></a>接続を確立の試行中にエラーが発生しました
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  このエラーは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がインストールされていないサーバーで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データのクエリを実行した場合に発生します。 SQL Server Analysis Services の場合にも発生 ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) サービスを停止すると、表示しようとしている場合、または[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]以前のバージョンからのデータ。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|データ接続に失敗しました。|  
|メッセージ テキスト|外部データ ソースへの接続を確立しようとしましたが、エラーが発生しました。 次の接続の更新に失敗しました:[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ|  
  
## <a name="explanation"></a>説明  
 Excel Services は、クエリを実行するときにこのエラーを返します[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]SharePoint、および SharePoint 環境にパブリッシュされた Excel ブック内のデータはありません、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバー、または SQL Server の Analysis Services ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])サービスが停止しました。  
  
 このエラーは、クエリ エンジンを使用できないときに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データのスライスまたはフィルター処理を行うと発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をインストールするか、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がインストールされた SharePoint 環境に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを移動します。 詳細については、「 [PowerPivot for SharePoint 2010 のインストール](http://msdn.microsoft.com/8d47dde7-c941-4280-a934-e2fe3f9a938f)」を参照してください。  
  
 ソフトウェアがインストールされている場合、SQL Server Analysis Services のことを確認します ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) インスタンスが実行されています。 サーバーの全体管理で、 **[サーバーのサービスの管理]** を確認します。 また、管理ツールの [サービス] コンソール アプリケーションも確認します。  
  
 SQL Server 2008 R2 バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成された [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックの場合、SQL Server 2008 R2 バージョンの Analysis Services OLE DB プロバイダーをインストールする必要があります。 プロバイダーをインストールし、Microsoft.AnalysisServices.ChannelTransport.dll ファイルを登録しなかった場合、このエラーが発生します。 ファイルの登録の詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ接続では Windows 認証を使用しており、ユーザーの資格情報を借用できませんでした。次の接続の更新に失敗しました:Power Pivot データ](../../analysis-services/power-pivot-sharepoint/the-data-connection-user-could-not-be-delegated.md)  
  
  
