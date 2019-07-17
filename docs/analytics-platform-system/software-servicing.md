---
title: ソフトウェアのサービス、Analytics Platform System |Microsoft Docs
description: Analytics Platform System (APS) でソフトウェアにサービスを提供します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 97f0ccaed9cded73241f473d81400b30acbe402c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960088"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Analytics Platform System でソフトウェアのサービス
このセクションでは、サービスの要件の WSUS と Analytics Platform System の修正プログラムを含めて、Analytics Platform System アプライアンス ソフトウェアをまとめたものです。  
  
## <a name="Basics"></a>ソフトウェア サービスの基礎  
**WSUS:** Analytics Platform System appliance では、Windows Server Update Services (WSUS) から更新プログラムを受信するように構成する必要があります。 これらの更新プログラムには、アプライアンス ソフトウェアの重要な変更が含まれます。 構成されている多くの更新プログラムは自動的にインストールされ、実践的な管理は必要ありません。 通常、WSUS の更新プログラムは、中に構成された、 [Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41; ](configure-windows-server-update-services-wsus.md)新しいアプライアンスのセットアップ中に手順を実行します。 有効でない場合は、この構成手順を後で実行できます。 WSUS については、次を参照してください。、 [WSUS web サイト ガイド](https://go.microsoft.com/fwlink/?LinkId=202417)します。  
  
**修正プログラム:** さらに、Analytics Platform System の修正プログラムを適用する必要があります。 A*修正プログラム*Analytics Platform System のソフトウェアの問題を解決するのには、特定の顧客用に作成したソフトウェアの更新します。 各修正プログラムは、顧客固有の問題の修正プログラムをインストールする実行可能ファイルです。 各修正プログラムには、Windows、SQL Server および Analytics Platform System のすべての以前にリリースされたソフトウェア更新プログラムの集積/離散も含まれています。 修正プログラムをインストールする場合は、Microsoft サポートが修正プログラムと手順を提供するは。  
  
**更新プログラムのスコープ:** Analytics Platform System に修正プログラムまたはサービス パックを適用する必要がありますをオフラインに全体のアプライアンスです。  
  
**SSIS 変換先アダプターとクライアント ツール:** SSIS 変換先アダプター MSI への変更が含まれる修正プログラムを適用するときに、または MSI ファイルは更新のクライアント ツールの MSI、 **C:\PDWINST\ClientTools**ディレクトリ制御ノードにします。 修正プログラムが、更新された MSI ファイルからのコンポーネントを自動的にインストールされません。 これらのコンポーネントを更新するには、顧客は、コンポーネントの以前のバージョンをアンインストールして更新された MSI ファイルから新しいバージョンをインストールする必要があります。 SSIS 変換先アダプター MSI への変更が含まれる修正プログラムをアンインストールするときに、またはクライアント ツールの MSI をこれらのコンポーネントの MSI ファイルは、以前のバージョンに戻されます。 以前のバージョンにこれらのコンポーネントを元に戻すには、顧客は、コンポーネントの既存の (最新) バージョンをアンインストールして、元に戻された MSI ファイルから以前のバージョンを再インストールする必要があります。  
  
## <a name="software-servicing-topics"></a>ソフトウェアのサービスに関するトピック  
次のトピックでは、アプライアンス上でソフトウェアのサービスを管理する方法について説明します。  
  
-   [ダウンロードして Microsoft 更新プログラムを適用して&#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Microsoft 更新プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
  
-   [Analytics Platform System の修正プログラムを適用&#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Analytics Platform System の修正プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
