---
title: カスタム ログ プロバイダーの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: af3478e254f01f7cf53d5a09b6febab3b1e85e8b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176304"
---
# <a name="developing-a-custom-log-provider"></a>カスタム ログ プロバイダーの開発
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、パッケージの実行中に発生したイベントをキャプチャできるようにする広範なログ記録機能があります。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、さまざまなログ プロバイダーを使用でき、ログを作成して XML、テキスト、データベースなどの形式で保存したり、Windows イベント ログに格納したりできます。 提供されるログ プロバイダーと出力形式が、要件を必ずしも満たさない場合は、カスタム ログ プロバイダーを作成できます。

 カスタム ログ プロバイダーを作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性を適用し、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティや <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。

## <a name="in-this-section"></a>このセクションの内容
 ここでは、カスタム ログ プロバイダーを作成、構成、およびコーディングする方法について説明します。

 [カスタムログプロバイダーの作成](creating-a-custom-log-provider.md)カスタムログプロバイダープロジェクトのクラスを作成する方法について説明します。

 [カスタムログプロバイダーのコーディング](coding-a-custom-log-provider.md)基本クラスのメソッドとプロパティをオーバーライドすることによって、カスタムログプロバイダーを実装する方法について説明します。

 [カスタムログプロバイダーのユーザーインターフェイスの開発](developing-a-user-interface-for-a-custom-log-provider.md)カスタムログプロバイダーのカスタムユーザーインターフェイスは、で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]はサポートされていません。

## <a name="related-topics"></a>関連トピック

### <a name="information-common-to-all-custom-objects"></a>すべてのカスタム オブジェクトに共通の情報
 
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。

 [Integration Services 用のカスタムオブジェクトの開発](../developing-custom-objects-for-integration-services.md)のすべての種類のカスタムオブジェクトを実装するため[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]の基本的な手順について説明します。

 [カスタムオブジェクトの永続](../persisting-custom-objects.md)化カスタムの永続性について説明し、必要な場合について説明します。

 [カスタムオブジェクトのビルド、配置、およびデバッグ](../building-deploying-and-debugging-custom-objects.md)カスタムオブジェクトのビルド、署名、配置、およびデバッグの手法について説明します。

### <a name="information-about-other-custom-objects"></a>その他のカスタム オブジェクトに関する情報
 
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。

 [カスタムタスクの開発](../task/developing-a-custom-task.md)カスタムタスクをプログラミングする方法について説明します。

 [カスタム接続マネージャーの開発](../connection-manager/developing-a-custom-connection-manager.md)カスタム接続マネージャーをプログラミングする方法について説明します。

 [カスタム ForEach 列挙子の開発](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)カスタム列挙子をプログラミングする方法について説明します。

 [カスタムデータフローコンポーネントの開発](../data-flow/developing-a-custom-data-flow-component.md)カスタムデータフローの変換元、変換、および変換先をプログラミングする方法について説明します。

![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services に関するページを参照してください。](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。


