---
title: スクリプトによるパッケージの拡張 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b060579cfb55a1698007630240f86bdf4c170c5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229272"
---
# <a name="extending-packages-with-scripting"></a>スクリプトによるパッケージの拡張
  組み込みコンポーネントの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が要件を満たしていない場合は、独自の拡張機能をコーディングすることによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の機能を拡張できます。 パッケージを拡張するには 2 つの方法があります。1 つ目は、スクリプト タスクおよびスクリプト コンポーネントによって提供される強力なラッパー内でコードを記述する方法です。2 つ目は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルによって提供される基本クラスを基にカスタム [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 拡張機能を最初から作成する方法です。  
  
 ここでは、より簡単な方法である、スクリプトを使用したパッケージの拡張について説明します。  
  
 スクリプト タスクおよびスクリプト コンポーネントを利用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローとデータ フローを、コードをほとんど記述することなく拡張できます。 これらの両オブジェクトでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 開発環境と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のプログラミング言語を使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリやカスタム アセンブリで提供されるすべての機能を活用できます。 スクリプト タスクおよびスクリプト コンポーネントを使用すると、カスタム タスクやカスタム データ フロー コンポーネントの開発時に通常必要となるインフラストラクチャ コードを一切記述せずにカスタム機能を作成できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [スクリプト タスクとスクリプト コンポーネントの比較](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
 スクリプト タスクとスクリプト コンポーネントの共通点および相違点について説明します。  
  
 [スクリプティング ソリューションとカスタム オブジェクトとの比較](comparing-scripting-solutions-and-custom-objects.md)  
 スクリプティング ソリューションとカスタム オブジェクトの開発のいずれかを選択する際に使用する基準について説明します。  
  
 [スクリプティング ソリューションでの他のアセンブリの参照](referencing-other-assemblies-in-scripting-solutions.md)  
 スクリプティング プロジェクトで外部アセンブリと名前空間を参照および使用するために必要な手順について説明します。  
  
 [スクリプト タスクによるパッケージの拡張](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md)  
 スクリプト タスクを使用してカスタム タスクを作成する方法について説明します。 通常は、パッケージの実行またはパッケージが開くデータ ソースごとにタスクが 1 回呼び出されます。  
  
 [スクリプト コンポーネントによるデータ フローの拡張](data-flow-script-component/extending-the-data-flow-with-the-script-component.md)  
 スクリプト コンポーネントを使用して、カスタム データ フローの変換元、変換、および変換先を作成する方法について説明します。 通常は、処理するデータ行ごとにデータ フロー コンポーネントが 1 回呼び出されます。  
  
## <a name="reference"></a>リファレンス  
 [Integration Services のエラーとメッセージのリファレンス](../integration-services-error-and-message-reference.md)  
 事前に定義されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードと、そのシンボル名および説明の一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [カスタム オブジェクトを使用したパッケージの拡張](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 複数のパッケージで使用するプログラム カスタム タスク、データ フロー コンポーネント、およびその他のパッケージ オブジェクトを作成する方法について説明します。  
  
 [プログラムによるパッケージの作成](../building-packages-programmatically/building-packages-programmatically.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージをプログラムで作成、構成、実行、読み込み、保存、および管理する方法を説明します。  
  
![Integration Services のアイコン (小)](../media/dts-16.gif "Integration Services アイコン (小)")**Integration Services の日付を維持します。** <br /> 最新のダウンロード、アーティクル、サンプル、およびビデオの[!INCLUDE[msCoName](../../includes/msconame-md.md)]、およびコミュニティで選択されたソリューションを参照してください、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] msdn ページ。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
