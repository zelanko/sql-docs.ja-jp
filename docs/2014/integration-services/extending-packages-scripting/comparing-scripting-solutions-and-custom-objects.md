---
title: スクリプティング ソリューションとカスタム オブジェクトとの比較 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 18c78f2ba914dc5b65bba9d11de2a697c7038d5c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968420"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a>スクリプティング ソリューションとカスタム オブジェクトとの比較
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] スクリプト タスクまたはスクリプト コンポーネントは、カスタム マネージド タスクまたはデータ フロー コンポーネントで使用できる機能とほぼ同じ機能を実装できます。 ここでは、適切な種類のタスクを必要に応じて選択するときに役立つ注意事項について説明します。  
  
-   構成または機能が個々のパッケージに固有である場合は、カスタム オブジェクトを開発する代わりに、スクリプト タスクまたはスクリプト コンポーネントを使用します。  
  
-   機能が汎用で、将来は他のパッケージ用に使用されたり、他の開発者が使用する可能性がある場合は、スクリプト ソリューションを使用する代わりに、カスタム オブジェクトを作成します。 カスタム オブジェクトは任意のパッケージで使用できますが、スクリプトは、そのスクリプトが作成されたパッケージでのみ使用できます。  
  
-   同じパッケージ内でコードを再使用する場合、カスタム オブジェクトを作成することを検討します。 あるスクリプト タスクまたはコンポーネントから別のスクリプト タスクまたはコンポーネントにコードをコピーすると、コードの複数コピーの維持および更新が煩雑になるため、管理が難しくなります。  
  
-   将来的に実装方法を変更する場合は、カスタム オブジェクトの使用を検討します。 カスタム オブジェクトは、親パッケージとは別に開発および配置できますが、スクリプト ソリューションを更新する場合は、パッケージ全体を再配置する必要があります。  
  
![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [カスタム オブジェクトを使用したパッケージの拡張](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
