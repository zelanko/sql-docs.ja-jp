---
title: 分析管理オブジェクト (AMO) を使用した開発 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: edd91a0d4608f03dd622ef2b25820d10f9b4f455
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="developing-with-analysis-management-objects-amo"></a>分析管理オブジェクト (AMO) による開発
分析管理オブジェクト (AMO) は、アプリケーションを実行中のインスタンスを管理できるようにするプログラムでアクセスされるオブジェクトの完全なライブラリ[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。

ここでは、AMO の概念について説明します。AMO の主要オブジェクトに焦点を絞り、それらをいつどのように使用するか、それらが互いにどのように関係しているかについて解説します。 特定のオブジェクトまたはクラスの詳細についてを参照してください。

- [Microsoft.AnalysisServices Namespace](http://msdn.microsoft.com/library/microsoft.analysisservices.aspx)、リファレンス ドキュメントについて
- [Analysis Services 管理オブジェクト (AMO)](http://www.bing.com/search?q=Analysis+Services+Management+Objects+%28AMO%29)、Bing.com 一般的な検索とします。


 **SQL Server 2016 の新機能**

SQL Server 2016 では、AMO は複数のアセンブリにリファクターされています。 ジェネリック クラスでは、サーバー、データベース、およびロールなど、 **Microsoft.AnalysisServices.Core** Namespace です。 多次元の固有の Api のままに[Microsoft.AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720.aspx)です。

カスタム スクリプトおよび AMO の以前のバージョンに対して記述されたアプリケーションは、まま変更せずに機能し続けます。 ただしがあればスクリプトまたはアプリケーションを対象とする SQL Server 2016 具体的には、またはカスタム ソリューションを再構築する必要がある場合、必ず、新しいアセンブリと名前空間をプロジェクトに追加します。

## <a name="see-also"></a>参照
[Services スクリプト言語の分析の使用による開発&#40;ASSL&#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)
[Analysis Services の XMLA による開発](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)
