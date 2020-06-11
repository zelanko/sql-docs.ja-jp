---
title: 'ブック内のデータ接続に関するデータを更新できません。 再試行するか、システム管理者に問い合わせてください。 次の接続を更新できませんでした: PowerPivot Data |Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 81a72e0009659e06fd27e9c402f17ddab259d228
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84540178"
---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook-try-again-or-contact-your-system-administrator-the-following-connections-failed-to-refresh-powerpivot-data"></a>ブック内のデータ接続に関するデータを更新できません。 再試行するか、システム管理者に問い合わせてください。 次の接続の更新に失敗しました:PowerPivot データ
  PowerPivot データを含む Excel ブックで、Excel Services は、PowerPivot サーバーに送信した接続要求が失敗した場合にこのエラーを返します。  
  
## <a name="details"></a>詳細情報  
  
|||  
|-|-|  
|適用対象:|PowerPivot for SharePoint のインストール|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|以下を参照してください。|  
|メッセージ テキスト|ブック内のデータ接続に関するデータを更新できません。 再試行するか、システム管理者に問い合わせてください。 次の接続の更新に失敗しました:PowerPivot データ|  
  
## <a name="explanation-and-resolution"></a>説明および解決方法  
 Excel Services が PowerPivot データに接続できないか、PowerPivot データを読み込むことができません。 このエラーは、次のような状況で発生します。  
  
 **シナリオ 1: サービスが開始されていない**  
  
 SQL Server Analysis Services (PowerPivot) インスタンスが開始されていません。 パスワードの期限が切れると、サービスの実行が停止します。 パスワードの変更の詳細については、「 [PowerPivot サービスアカウントの構成](configure-power-pivot-service-accounts.md)」および「 [PowerPivot for SharePoint サーバーの開始または停止](start-or-stop-a-power-pivot-for-sharepoint-server.md)」を参照してください。  
  
 **シナリオ 2a: サーバー上で以前バージョンのブックを開こうとしている**  
  
 開こうとしているブックが、SQL Server 2008 R2 バージョンの PowerPivot for Excel で作成された可能性があります。 ほとんどの場合、データ接続文字列で指定された Analysis Services データ プロバイダーは、要求を処理しているコンピューター上に存在しません。  
  
 このような場合は、ULS ログに "ブック ' ' の ' PowerPivot データ ' の更新に失敗しました" というメッセージが表示され、 \<URL to workbook> その後に "接続を取得できません" というメッセージが表示されます。  
  
 ブックのバージョンを決定するには、Excel で開き、接続文字列にどのデータ プロバイダーが指定されているか確認します。 SQL Server 2008 R2 ブックは、MSOLAP.4 をデータ プロバイダーとして使用します。  
  
 この問題を回避するために、ブックをアップグレードすることができます。 または、以下の方法で PowerPivot for SharePoint または Excel Services を実行している物理コンピューター上の SQL Server 2008 R2 バージョンの Analysis Services からクライアント ライブラリをインストールすることができます。  
  
 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 **シナリオ 2b: 間違ったバージョンのクライアント ライブラリがインストールされたアプリケーション サーバーで Excel Services が実行されている**  
  
 既定では、SharePoint Server 2010 は、SQL Server 2008 バージョンの Analysis Services OLE DB プロバイダーを Excel Services を実行するアプリケーション サーバーにインストールします。 PowerPivot データ アクセスをサポートするファームでは、Excel Services や PowerPivot for SharePoint など、PowerPivot データを要求するアプリケーションを実行するすべての物理サーバーは、最新バージョンのデータ プロバイダーを使用する必要があります。  
  
 PowerPivot for SharePoint を実行するサーバーは、更新された OLE DB データ プロバイダーを自動的に取得します。 同じコンピューター上の PowerPivot for SharePoint を使用しない、スタンドアロン インスタンスの Excel Services など、その他のサーバーは、新しいクライアント ライブラリを使用するために、更新プログラムを適用する必要があります。 「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)」を参照してください。  
  
 **シナリオ 3: ドメイン コントローラーを使用できない**  
  
 ユーザー ID の検証にドメイン コントローラーを使用できないことが原因である場合があります。 Windows トークン サービスに対するクレームにより各接続で SharePoint ユーザーを認証するには、ドメイン コントローラーが必要です。 Windows トークン サービスに対するクレームでは、キャッシュされた資格情報は使用されません。 接続ごとにユーザー ID が検証されます。  
  
 SharePoint ログ ファイルを表示して、このエラーの原因を確認できます。 SharePoint ログに、"IClaimsIdentity から WindowsIdentity を取得できませんでした" というメッセージがある場合、ユーザー ID を認証できなかったことを示します。  
  
 この問題を回避するには、PowerPivot サーバーと同じドメインにコンピューターを所属させるか、ローカル コンピューターにドメイン コントローラーをインストールします。 2 番目の解決策として、ドメイン コントローラーのインストールを行う場合は、すべてのサービスとユーザーのローカル ドメイン アカウントを作成することが必要になります。 それには、サービス アカウントを構成して、定義したアカウントの SharePoint 権限を構成する必要があります。  
  
 PowerPivot for SharePoint をオフライン状態で使用することを目的とする場合は、コンピューターにドメイン コントローラーをインストールすると便利です。 PowerPivot をオフラインで使用する方法の詳細については、「」のブログ記事「PowerPivot サーバーをネットワークから切断する」を参照してください [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241) 。  
  
 **シナリオ 4: 不安定なサーバー**  
  
 1 つ以上のサービスが一貫性のない状態にある可能性があります。 IISRESET を実行すると問題が解決することがあります。  
  
  
