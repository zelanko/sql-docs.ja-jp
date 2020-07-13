---
title: カスタム ForEach 列挙子用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 53a7234949b382edef90b8f07923045438a8cf4f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427479"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>カスタム ForEach 列挙子用ユーザー インターフェイスの開発
  基本クラスのプロパティとメソッドをオーバーライドしてカスタム機能を実装したら、Foreach 列挙子用のカスタム ユーザー インターフェイスを作成します。 カスタム ユーザー インターフェイスを作成しない場合、ユーザーは [プロパティ] ウィンドウを使用して新しいカスタム Foreach 列挙子を構成することしかできません。  
  
 カスタム ユーザー インターフェイスのプロジェクトまたはアセンブリで、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI> を実装するクラスを作成します。 このクラスは、通常他の Windows フォーム コントロールをホストするための複合コントロールの作成に使用される System.Windows.Forms.UserControl から派生します。 作成するコントロールは、**[Foreach ループ エディター]** の **[コレクション]** タブの **[列挙子の構成]** 領域に表示されます。  
  
> [!IMPORTANT]  
>  「[Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md)」(カスタム オブジェクトのビルド、配置、およびデバッグ) で説明されているようにカスタム ユーザー インターフェイスに署名してビルドし、グローバル アセンブリ キャッシュにインストールしたら、このクラスの完全修飾名を <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> プロパティで忘れずに指定してください。  
  
## <a name="coding-the-user-interface-control-class"></a>ユーザー インターフェイス コントロール クラスのコーディング  
  
### <a name="initializing-the-user-interface"></a>ユーザー インターフェイスの初期化  
 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> メソッドをオーバーライドして、ホスト オブジェクトへの参照、接続マネージャーのコレクションへの参照、およびパッケージで定義された変数をキャッシュします。  
  
### <a name="setting-properties-on-the-user-interface-control"></a>ユーザー インターフェイス コントロールでのプロパティの設定  
 ユーザー インターフェイス クラスの派生元である UserControl クラスは、他の Windows フォーム コントロールをホストするための複合コントロールとして使用することを目的としています。 このクラスが他のコントロールをホストするため、コントロールをドラッグ アンド ドロップし、それらを並べ替え、プロパティを設定し、すべての Windows フォーム アプリケーションと同じようにコントロールのイベントに実行時に応答することにより、カスタム ユーザー インターフェイスをデザインできます。  
  
### <a name="saving-settings"></a>設定の保存  
 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> メソッドをオーバーライドして、ユーザーがエディターを終了したときに、ユーザーが選択した値をコントロールから列挙子のプロパティにコピーします。  
  
![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>関連項目  
 [カスタム Foreach 列挙子の作成](creating-a-custom-foreach-enumerator.md)   
 [カスタム Foreach 列挙子のコーディング](coding-a-custom-foreach-enumerator.md)  
  
  
