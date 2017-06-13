---
title: "IRenderingExtension インターフェイスを実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
caps.latest.revision: 43
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3b5772901cfaabedab1b42db39dcd85c49119509
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-the-irenderingextension-interface"></a>IRenderingExtension インターフェイスの実装
  表示拡張機能では、実際のデータと組み合わされるレポート定義から出力結果を取得し、その結果データを使用可能な形式で表示します。 組み合わされたデータの変換と書式設定は、<xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> を実装する共通言語ランタイム (CLR) クラスを使用して実行されます。 これにより、オブジェクト モデルは、ビューアーやプリンターなどの出力先で使用できる出力形式に変換されます。  
  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> には、コーディングが必要なメソッドが 3 つあります。  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> : レポートを表示します。  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> : レポートの特定のストリームを表示します。  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> : アイコンなどのレポートに必要な追加情報を取得します。  
  
 ここでは、これらのメソッドについて詳しく説明します。  
  
## <a name="render-method"></a>Render メソッド  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> メソッドには、次のオブジェクトを表す引数が含まれます。  
  
-   *レポート*をレンダリングします。 このオブジェクトには、レポートのプロパティ、データ、およびレイアウト情報が含まれます。 レポートは、レポート オブジェクト モデル ツリーのルートです。  
  
-   *ServerParameters*存在する場合、文字列辞書オブジェクト、およびレポート サーバーのパラメーターが含まれています。  
  
-   *DeviceInfo*デバイス設定を含むパラメーター。 詳細については、次を参照してください。[表示拡張機能にデバイス情報設定を渡す](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)です。  
  
-   *ClientCapabilities*パラメーターが含まれている<xref:System.Collections.Specialized.NameValueCollection>を表示するには、クライアントに関する情報を持つディクショナリ オブジェクトです。  
  
-   *RenderProperties*表示結果に関する情報を格納します。  
  
-   *CreateAndRegisterStream*に表示するためにストリームを取得するために呼び出すデリゲート関数。  
  
### <a name="deviceinfo-parameter"></a>deviceInfo パラメーター  
 *DeviceInfo*パラメーターには、表示パラメーターが含まれています。、パラメーターをレポートしません。 表示パラメーターは表示拡張機能に渡されます。 *DeviceInfo*値に変換、<xref:System.Collections.Specialized.NameValueCollection>レポート サーバーでのオブジェクト。 項目を*deviceInfo*パラメーターは大文字と小文字の値として扱われます。 URL による表示要求が行われる場合にアクセスするフォームの URL パラメーター`rc:key=value`キーと値のペアに変換されます、 *deviceInfo*ディクショナリ オブジェクトです。 ブラウザー検出コードは、次のアイテムも用意されています。、 *clientCapabilities*ディクショナリ: ある EcmaScriptVersion、JavaScript、MajorVersion、MinorVersion、Win32、種類、および AcceptLanguage です。 いずれかの名前と値のペア、 *deviceInfo*表示拡張機能によって認識されないパラメーターは無視されます。 次のコード サンプルは、アイコンを取得する <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> メソッドを示します。  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a>RenderStream メソッド  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> メソッドは、レポート内の特定のストリームを表示します。 最初の <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 呼び出しですべてのストリームが作成されますが、ストリームは最初はクライアントに返されません。 このメソッドは、HTML 表示における画像などのセカンダリ ストリームや、画像 (EMF) などの複数ページ表示拡張機能の追加ページに使用します。  
  
## <a name="getrenderingresource-method"></a>GetRenderingResource メソッド  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> メソッドは、レポート全体を表示せずに情報を取得します。 レポートに情報は必要だが、レポート自体を表示する必要がない場合があります。 たとえば、アイコンの表示拡張機能に関連付けられている場合は、使用、 *deviceInfo*パラメーターの 1 つのタグを含んでいる**\<アイコン >**です。 このような場合に、<xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> メソッドを使用できます。  
  
## <a name="see-also"></a>参照  
 [表示拡張機能を実装します。](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [表示拡張機能の概要](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
  
  
