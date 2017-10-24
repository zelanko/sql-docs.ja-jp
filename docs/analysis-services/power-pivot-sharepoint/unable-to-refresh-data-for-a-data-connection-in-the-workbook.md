---
title: "ブック内のデータ接続のデータを更新できません |。Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e92a6ac8d430b88c18ecae14c2a52771b566d39d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook"></a>ブック内のデータ接続に関するデータを更新できません
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含む Excel ブックで、Excel Services は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーに送信した接続要求が失敗した場合にこのエラーを返します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint インストール|  
|[製品バージョン]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|下記を参照。|  
|メッセージ テキスト|ブック内のデータ接続に関するデータを更新できません。 再試行するか、システム管理者に問い合わせてください。 以下の接続を更新できませんでした: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ|  
  
## <a name="explanation-and-resolution"></a>説明および解決方法  
 Excel Services が [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに接続できないか、Power Pivot データを読み込むことができません。 このエラーは、次のような状況で発生します。  
  
 **シナリオ 1: サービスが開始されていない**  
  
 SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) インスタンスが開始されていません。 パスワードの期限が切れると、サービスの実行が停止します。 パスワードの変更方法の詳細については、「 [Power Pivot サービス アカウントの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md) 」および「 [PowerPivot for SharePoint サーバーの開始または停止](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md)」を参照してください。  
  
 **シナリオ 2a: サーバー上で以前バージョンのブックを開こうとしている**  
  
 開こうとしているブックが、SQL Server 2008 R2 バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成された可能性があります。 ほとんどの場合、データ接続文字列で指定された Analysis Services データ プロバイダーは、要求を処理しているコンピューター上に存在しません。  
  
 大文字と小文字の場合は、ULS ログにこのメッセージが表示されます:"の更新に失敗しました '[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]t データ' ブックで '\<ブックへの URL >'"、「接続を取得できません」という順です。  
  
 ブックのバージョンを決定するには、Excel で開き、接続文字列にどのデータ プロバイダーが指定されているか確認します。 SQL Server 2008 R2 ブックは、MSOLAP.4 をデータ プロバイダーとして使用します。  
  
 この問題を回避するために、ブックをアップグレードすることができます。 または、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint または Excel Services を実行している物理コンピューター上の SQL Server 2008 R2 バージョンの Analysis Services からクライアント ライブラリをインストールできます。詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。  
  
 **シナリオ 2b: 間違ったバージョンのクライアント ライブラリがインストールされたアプリケーション サーバーで Excel Services が実行されている**  
  
 既定では、SharePoint Server 2010 は、SQL Server 2008 バージョンの Analysis Services OLE DB プロバイダーを Excel Services を実行するアプリケーション サーバーにインストールします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスをサポートするファームでは、Excel Services や [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint など、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを要求するアプリケーションを実行するすべての物理サーバーは、最新バージョンのデータ プロバイダーを使用する必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を実行するサーバーは、更新された OLE DB データ プロバイダーを自動的に取得します。 同じコンピューター上の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を使用しない、スタンドアロン インスタンスの Excel Services など、その他のサーバーは、新しいクライアント ライブラリを使用するために、更新プログラムを適用する必要があります。 詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。  
  
 **シナリオ 3: ドメイン コントローラーを使用できない**  
  
 ユーザー ID の検証にドメイン コントローラーを使用できないことが原因である場合があります。 Windows トークン サービスに対するクレームにより各接続で SharePoint ユーザーを認証するには、ドメイン コントローラーが必要です。 Windows トークン サービスに対するクレームでは、キャッシュされた資格情報は使用されません。 接続ごとにユーザー ID が検証されます。  
  
 SharePoint ログ ファイルを表示して、このエラーの原因を確認できます。 SharePoint ログに、"IClaimsIdentity から WindowsIdentity を取得できませんでした" というメッセージがある場合、ユーザー ID を認証できなかったことを示します。  
  
 この問題を回避するには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーと同じドメインにコンピューターを所属させるか、ローカル コンピューターにドメイン コントローラーをインストールします。 2 番目の解決策として、ドメイン コントローラーのインストールを行う場合は、すべてのサービスとユーザーのローカル ドメイン アカウントを作成することが必要になります。 それには、サービス アカウントを構成して、定義したアカウントの SharePoint 権限を構成する必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をオフライン状態で使用することを目的とする場合は、コンピューターにドメイン コントローラーをインストールすると便利です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] をオフラインで使用する方法の詳細については、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] http://www.powerpivotgeek.com [で "](http://go.microsoft.com/fwlink/?LinkId=184241)サーバーのオフライン化" に関するブログ エントリを参照してください。  
  
 **シナリオ 4: 不安定なサーバー**  
  
 1 つ以上のサービスが一貫性のない状態にある可能性があります。 IISRESET を実行すると問題が解決することがあります。  
  
  

