---
title: フォルダーへのファイルのアップロード | Microsoft Docs
description: Reporting Services でファイル システムからさまざまなファイルの種類をアップロードし、レポート サーバー データベースに監視対象アイテムとして格納するしくみについて説明します。
ms.date: 06/17/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 94de4754811e1cb35c819b9cf8f4398b9e8c8634
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547854"
---
# <a name="upload-files-to-a-folder"></a>フォルダーへのファイルのアップロード
  ファイル システムからファイルをアップロードし、それらを管理対象アイテムとしてレポート サーバー データベースに格納できます。 ファイルのアップロード時に行われる処理は、ファイルの種類によって異なります。  
  
-   .rdl ファイルのアップロードは、レポートのパブリッシュと同等です。  
  
-   その他のファイルをアップロードすると、アップロードしたファイルが単一のバイナリ オブジェクトとしてレポート サーバー データベースに追加されます。 これらのファイルは、リソースとしてレポート サーバーにパブリッシュされます。 リソースのファイルの種類には指定がありません。 ファイルの拡張子が既知の MIME の種類に一致する場合、リソースの種類を識別するために、その MIME の種類のアイコンが使用されます。 ファイルの拡張子が未登録の場合、リソースは汎用ファイル アイコンで示されます。  
  
    >[!NOTE]  
    >レポート データ ソース (.rds) ファイルをアップロードして共有データ ソースを作成することはできません。 .rds ファイルは、レポート デザイナーでのみ使用されます。 Web ポータルを使って定義および管理する共有データ ソース アイテムのコンテンツを提供することはできません。 アップロードする代わりに、.rds ファイルを基に共有データ ソースを作成するスクリプトを記述することができます。  
  
 アップロードするアイテムの最大ファイル サイズは 2 GB です。これは [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の MaxFileSizeMb プロパティで設定できます。  
  
 視覚的には、レポート サーバー データベースにアップロードしたファイルは、以下のアイコンでフォルダー階層に表示されます。  
  
  ![レポート サーバーのアップロード可能ファイル アイコン](../../reporting-services/report-server/media/upload-files-to-a-folder/report-server-uploadable-file-icons.png)
  
 ファイルをアップロードすると、ファイルは常に、現在選択しているフォルダーに格納されます。 最初に、アイテムを含めるフォルダーに移動できます。また、ファイルをアップロードしてから最終的な場所にファイルを移動することもできます。  
  
 ファイルをアップロードするには、Web ポータルを使用します。 レポート サーバーにファイルをアップロードできるかどうかは、ロールの割り当てを構成するタスクによって異なります。 既定のセキュリティを使用している場合は、ローカル管理者によってレポート サーバーにアイテムを追加できます。 個人用レポートが有効である場合は、個人用レポート フォルダーを持っているすべてのユーザーに、そのフォルダーへアイテムをアップロードする権限が与えられます。 カスタム ロールの割り当てを使用している場合は、フォルダー管理をサポートするタスクがロールの割り当てに含まれている必要があります。  
  
|目的|含まれるタスク|  
|----------------|-------------------------|  
|.rdl ファイルをフォルダーにアップロード|レポートの管理|  
|任意のファイルをバイナリ オブジェクトとしてアップロード|リソースの管理|  
|フォルダーのコンテンツの表示|リソースの表示、レポートの表示|  
  
## <a name="see-also"></a>関連項目  
 [レポート サーバーの Web ポータル (SSRS ネイティブ モード)](../../reporting-services/web-portal-ssrs-native-mode.md)  
 [ネイティブ モードのレポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [タスクと権限](../../reporting-services/security/tasks-and-permissions.md)   
 [レポート サーバーでファイルまたはレポートをアップロードする](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)   
  