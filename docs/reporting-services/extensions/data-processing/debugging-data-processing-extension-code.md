---
title: "データ処理拡張機能コードのデバッグ |Microsoft ドキュメント"
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
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: 40
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7af6b33039d19029d1595ac08f5d5345cdaa1c58
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="debugging-data-processing-extension-code"></a>データ処理拡張機能コードのデバッグ
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]するのに役立ついくつかのデバッグ ツール、データ処理拡張機能のコードを分析エラーを探すことを示します。 最適なデバッグ ツールは、使用する目的によって異なります。 この例では [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]を使用します。  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>データ処理拡張機能コードをデバッグするには  
  
1.  [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] を起動し、データ処理拡張機能プロジェクトを開きます。  
  
2.  プロジェクトを構築し、データ処理拡張機能アセンブリと付随する .pdb ファイルをレポート デザイナーに配置します。 展開の詳細については、次を参照してください。[する方法: レポート デザイナーにデータ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)です。  
  
3.  データ処理拡張機能コードを [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で開いたまま、別の [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ウィンドウで新しいレポート プロジェクトを開きます。  
  
4.  データ処理拡張機能プロジェクトを含む [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のウィンドウに移動し、コードにブレーク ポイントを設定します。  
  
5.  データ処理拡張機能プロジェクト ウィンドウをアクティブのまま、をクリックして**プロセスにアタッチする**上、**デバッグ**メニュー。  
  
     **プロセスにアタッチする**ダイアログ ボックスが開きます。  
  
6.  、プロセスの一覧から、レポート プロジェクトに対応する devenv.exe プロセスを選択し、をクリックして**アタッチ**です。  
  
7.  使用してレポート データ ソースを定義する、**レポート データ**レポート プロジェクトのタブです。 通常、汎用クエリ デザイナーを使用してカスタム データ ソースへのクエリを実行します。 これにより、デバッガーが呼び出され、ブレーク ポイントに対応するコードが実行されます。  
  
8.  F11 キーを使用してコードを実行します。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用したデバッグの詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のマニュアルを参照してください。  
  
## <a name="see-also"></a>参照  
 [データ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
