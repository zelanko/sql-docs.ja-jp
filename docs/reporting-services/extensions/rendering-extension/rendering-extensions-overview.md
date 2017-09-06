---
title: "拡張機能の概要の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- formats [Reporting Services], rendering extensions
- rendering extensions [Reporting Services], about extensions
ms.assetid: 909356a0-4709-43e5-b597-33bd9bb22882
caps.latest.revision: 41
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: bf4ef7421e85e95d40a28803adec2c279b9a80bc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="rendering-extensions-overview"></a>表示拡張機能の概要
  表示拡張機能は、レポート サーバーのコンポーネントまたはモジュールで、レポートのデータとレイアウト情報をデバイス固有の形式に変換します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 7 つの表示拡張機能が含まれています: HTML、Excel、Word、CSV やテキスト、XML、イメージ、および PDF です。 追加の表示拡張機能を作成して、他の形式でレポートを生成できます。  
  
> [!NOTE]  
>  どの表示拡張機能を利用できるかは、RSReportServer.config ファイルのインストール済み拡張機能の一覧で確認できます。  
  
 次の表は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が備えている表示拡張機能の説明です。  
  
|Extension Name|Description|  
|--------------------|-----------------|  
|**XML**|XML 形式でレポートを表示します。 レポートは任意のブラウザーで開きます。 この XML 出力にさらに手を加えれば、新しい表示拡張機能を開発しなくても、必要な表示拡張機能を効率的に追加することができます。|  
|**CSV**|コンマ区切り形式でレポートを表示します。 レポートは、CSV ファイル形式に関連付けられている表示ツールで開きます。|  
|**IMAGE**|ページ指向形式でレポートを表示します。 この形式は、レポート ツール バーの [エクスポート] ボックスに **[TIFF]** と表示されます。|  
|**PDF**|Adobe Acrobat Reader 形式でレポートを表示します。 この形式は、レポート ツール バーの [エクスポート] ボックスに **[Acrobat (PDF) ファイル]** と表示されます。|  
|**EXCEL**|[!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)] 形式でレポートを表示します。|  
|**WORD**|レポートを [!INCLUDE[ofprword](../../../includes/ofprword-md.md)] で表示します。|  
|**HTML 4.0** (HTML 表示拡張機能の一部)|HTML は、初期状態でレポートを表示するのに使用される形式です。 ブラウザーが HTML4.0 をサポートしている場合は、HTML4.0 形式が使用されます。 それ以外の場合は、HTML 3.2 が使用されます。|  
|**MHTML** (HTML 表示拡張機能の一部)|MHTML 形式でレポートを表示します。 レポートは、Internet Explorer で開きます。 この形式は、レポート ツール バーの [エクスポート] ボックスに **[Web アーカイブ]** として表示されます。|  
|**NULL**|レポートを特定の形式で表示しません。 この表示拡張機能はレポートをキャッシュするのに有用です。 Null 表示形式は、スケジュールされた実行または配信と連動して使用する必要があります。|  
  
 推奨される形式とその使用方法の詳細については、次を参照してください。[レポートのエクスポート & #40 です。レポート ビルダーおよび SSRS &#41;](../../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md).  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] によって [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に実装された表示拡張機能は、すべて共通のインターフェイスを使用します。 これにより、すべての拡張機能で同じレベルの機能性が実装され、レポート サーバーのコア部分での表示処理用コードがより単純になります。  
  
## <a name="rendering-object-model"></a>表示オブジェクト モデル  
 レポートが処理されると、その処理結果は、表示オブジェクト モデル (ROM) として知られる、公開オブジェクト モデルになります。 この表示オブジェクト モデルは、処理されたレポートの内容、レイアウト、およびデータを定義するクラスのコレクションです。 開発者は、ROM を使用して、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム表示拡張機能を設計、開発、展開できます。 ROM は、レポートの XML 定義とユーザーにより定義されたレポート データが、レポート サーバーにより処理される際に作成されます。 処理が完了すると、表示拡張機能によりこの公開オブジェクト モデルが使用され、レポートの出力が定義されます。 ROM の利用可能なパブリック クラスが定義されている、 **Microsoft.ReportingServices.OnDemandReportRendering**名前空間。  
  
## <a name="writing-custom-rendering-extensions"></a>カスタム表示拡張機能の記述  
 カスタム表示拡張機能の作成を決める前に、より簡単な代替手段を評価する必要があります。 可能な代替手段としては以下の方法があります。  
  
-   既存の拡張機能のデバイス情報の設定を詳細に指定して、表示される出力をカスタマイズする。  
  
-   XML 表現形式の出力に XSL 変換 (XSLT) を組み合わせることで、カスタムの形式と表現機能を追加する。  
  
 カスタム表示拡張機能の記述は難しい作業です。 表示拡張機能は、一般的には、レポートの要素のあらゆる組み合わせをサポートする必要があり、多くのクラス、インターフェイス、メソッド、およびプロパティを実装しなければなりません。 場合に含まれていない形式でレポートをレンダリングする必要があります[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]表示拡張機能のコードを実装する必要があります、表示拡張機能のマネージ コード実装を独自に作成されることと、 **Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension**レポート サーバーに必要なインターフェイスです。  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に関する補足資料とホワイト ペーパーについては、[Reporting Services Web サイト](http://go.microsoft.com/fwlink/?LinkId=19951)の最新の技術文書を参照してください。  
  
## <a name="see-also"></a>参照  
 [表示拡張機能を実装します。](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
