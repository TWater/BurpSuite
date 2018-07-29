# BurpSuite

- [ Proxy 模块（代理模块）](#1)
- [ Target 模块（目标模块）](#2)
- [ Spider 模块（蜘蛛爬行）](#3)
- [ Scanner 模块（漏洞扫描）](#4)
- [ Intruder 模块（暴力破解）](#5)
- [ Repeater 模块（中继器）](#6)
- [ Sequencer 模块（定序器）](#7)
- [ Decoder 模块（编码模块）](#8)
- [1.语法示例](#5)
- [1.语法示例](#5)
- [1.语法示例](#5)
- [1.语法示例](#5)

<h2 id="1">Proxy 模块（代理模块）</h2>

### 一、简介
Proxy 代理模块作为 BurpSuite 的核心功能，拦截 HTTP/S 的代理服务器，作为一个在浏览器和目标应用程序之间的中间人，允许你拦截、查看、修改在两个方向上的原始数据流。

Burp 代理允许你通过监视和操纵应用程序传输的关键参数和其他数据来查找和探索应用程序的漏洞。通过以恶意的方式修改浏览器的请求，Burp 代理可以用来进行攻击，如：SQL 注入、cookie 欺骗、提升权限、会话劫持、目录遍历、缓冲区溢出。拦截的传输可以被修改成原始文本，也可以是包含参数或者消息头的表格，也可以十六进制形式，甚至可以操纵二进制形式的数据。在 Burp 代理可以呈现出包含 HTML 或者图像数据的响应消息。

### 二、模块说明
#### 1、Intercept
用于显示和修改 HTTP 请求和响应，通过你的浏览器和 Web 服务器之间。在 BurpProxy 的选项中，您可以配置拦截规则来确定请求是什么和响应被拦截（例如：范围内的项目、与特定文件扩展名、项目要求与参数等）。该面板还包含以下控制：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.1.png)

消息类型显示的四种格式:

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.2.png)

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.3.png)

- Change request method：对所有的请求，经过把所有相关的请求参数适当地搬迁到这个请求里来，你就可以自动地把请求的方法在 POST 和 GET 中间切换。通过发送恶意的请求使用这个选项来快速测试应用程序的极限参数是多少。
- Change body encoding：对于所有的请求，你可以在应用程序／X－WWW 格式的 URL 编码和多重表单/数据之间切换消息体的编码方式。
- Copy URL：把当前的 URL 完整地复制到粘贴板上。
- Cope to file：这个功能允许你把选择一个文件，并把消息的内容复制到这个文件里。这个对二进制数据来说是很方便的，要是通过粘贴板来复制会带来一些问题。复制操作是在选择的文本上进行的，如果没有被选中的内容，则是针对整个消息了。
- Pase form file：这个功能允许你选择一个文件，并把文件里的内容粘贴到消息里。这个对二进制数据来说是很方便的，要是通过粘贴板来复制会带来一些问题。粘贴操作会替换掉被选中的内容，如果没有内容被选中，则在光标位置插入这些内容。
- Save item：这个功能让你指定一个文件，把选中的请求和响应以 XML 的格式保存到这个文件，这里面包括所有的元数据如：响应的长度，HTTP 的状态码以及 MIME 类型。
- Don't intercept requests：通过这些命令可以快速地添加拦截动作的规则来阻止拦截到的消息，这些消息和当前的消息有着相同的特征(如远程主机、资源类型、响应编码)。
- Do intercept：仅对请求有效，这允许你可以对当请求和响应的进行强制拦截。
- Convert seiection：这些功能让你能够以多种方案对选择的文本进行快速的编码和解码。
- URL-encode as you type：如果这个选项被打开，你输入的像 & 和 = 这样的符号会被等价的 URL 编码代替。

#### 2、HTTP History
这个选项是来显示所有请求产生的细节，显示的有目标服务器和端口，HTTP 方法，URL ，以及请求中是否包含参数或被人工修改，HTTP 的响应状态码，响应字节大小，响应的 MIME 类型，请求资源的文件类型，HTML 页面的标题，是否使用 SSL ，远程 IP 地址，服务器设置的 cookies ，请求的时间。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.4.png)

双击某个请求即可打开详情,通过 Previous / next 可以快速切换请求，并且 Action 也可以将请求发送至其他模块。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.5.png)

可以通过最左边的列里的下拉菜单来加亮单个选项：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.6.png)

在历史记录表里，右击一个或多个选项，就会显示一个上下文菜单让你执行一些操作，包括修改目标范围，把这些选项发送到其他 Burp 工具，或者删除这些项：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.7.png)

还可以通过配置过滤器来确定哪些顶层的数据项显示在表格里。有效应用程序包含了大量的内容，如图像、CSS 等，这些有利于从视图上隐藏的。AJAX 应用程序产生大量相似的异步请求，你可能会想把他们从视图上过滤出来来查看一些感兴趣的项。在这个历史记录表的顶部有一个过滤栏。单击会有一个弹出窗口，让你来精准地配置显示哪些内容在表格里：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.8.png)

#### 3、WebSockets history
这个选项主要用于记录 WebSockets 的数据包，是 HTML5 中最强大的通信功能，定义了一个全双工的通信信道，只需 Web 上的一个 Socket 即可进行通信，能减少不必要的网络流量并降低网络延迟。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.9.png)

#### 4、Options
该选项主要用于设置代理监听、请求和响应、拦截反应、匹配和替换、ssl 等，其中有八大选项：Proxy Listeners 、Intercept Client Requests 、Intercept Server Responses 、Intercept WebSockets Messages 、Response Modification 、Match and replace 、SSL Pass Through 、Miscellaneous。

##### 选项1：Proxy Listeners
代理侦听器是侦听从您的浏览器传入的连接本地 HTTP 代理服务器。它允许您监视和拦截所有的请求和响应，并且位于 BurpProxy 的工作流的心脏。默认情况下，Burp 默认监听 12.0.0.1 地址，端口 8080 。要使用这个监听器，你需要配置你的浏览器使用 127.0.0.1 ：8080 作为代理服务器。此默认监听器是必需的测试几乎所有的基于浏览器的所有 Web 应用程序。

##### 选项2：Intercept Client Requests
配置拦截规则，设置拦截的匹配规则。当 Intercept request based on the following rules 为选中状态时，Burpsuite 会配置列表中的规则进行拦截或转发。

*注意：如果该复选框未选中，那么即使 Intercept is on 也无法截取数据包。*

*规则可以通过 Enabled 列中的复选框选择开启或关闭。*

*规则可以是域名，IP 地址，协议，HTTP 方法，URL ，文件扩展名，参数，cookie ，头/主体内容，状态代码，MIME 类型，HTML 页面标题等。*

*规则按顺序处理，并且使用布尔运算符 AND 和 OR 组合。*

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.10.png)

###### Add：添加一个新的代理地址。
1、Binding：新建一个代理。`Bind to port：`- 绑定端口号
`Bind to address：`- 绑定ip地址。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.11.png)

2、Request handling：这些设置包括选项来控制是否 BurpSuite 重定向通过此侦听器接收到的请求：

- `Redirect to host：`- 如果配置了这个选项，Burp 会在每次请求转发到指定的主机，而不必受限于览器所请求的目标。需要注意的是，如果你正使用该选项，则可能需要配置匹配／替换规则重写的主机中的请求，如果服务器中，您重定向请求预期，不同于由浏览器发送一个主机头。
- `Redirect to port：`- 如果配置了这个选项，Burp 会在每次请求转发到指定的端口，而不必受限于浏览。
- Force use of SSL - 如果配置了这个选项，Burp 会使用 HTTPS 在所有向外的连接，即使传入的请求中使用普通的 HTTP 。您可以使用此选项，在与 SSL 相关的响应修改选项结合，开展 sslstrip 般的攻击使用 Burp ，其中，强制执行 HTTPS 的应用程序可以降级为普通的 HTTP 的受害用户的流量在不知不觉中通过 BurpProxy 代理。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.12.png)

3、Certificate：这些设置控制呈现给客户端的 SSL 服务器的 SSL 证书。

- Generate CA-signed per-host certificate - 这是默认选项。安装后，BurpSuite 创造了一个独特的自签名的证书颁发机构（CA）证书，并将此计算机上使用，每次 BurpSuite 运行。当你的浏览器发出 SSL 连接到指定的主机，Burp 产生该主机，通过 CA 证书签名的 SSL 证书。您可以安装 BurpSuite 的 CA 证书作为在浏览器中受信任的根，从而使每个主机的证书被接受，没有任何警报。您还可以导出其他工具或 Burp 的其他实例使用 CA 证书。
- `Generate a CA-signed certificate with a specific hostname：`- 这类似于前面的选项；然而，Burp 会产生一个单一的主机证书与每一个 SSL 连接使用，使用您指定的主机名。在进行无形的代理时，此选项有时是必要的，因为客户端没有发送连接请求，因此 Burp 不能确定 SSL 协议所需的主机名。你也可以安装 BurpSuite 的 CA 证书作为受信任的根。
- `Use a custom certificate：`- 此选项使您可以加载一个特定的证书（在 PKCS＃12 格式）呈现给你的浏览器。如果应用程序使用它需要特定的服务器证书（例如一个给定序列号或证书链）的客户端应该使用这个选项。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.13.png)

###### Edit：编辑选中的代理地址。
###### Remove：删除选中代理地址。
##### 选项3：Intercept Server Responses
配置拦截规则，设置拦截的匹配规则，不过这个选项是基于服务端拦截，当选小的 Intercept request based on the following rules 为选中状态时，Burpsuite 会匹配响应包。

##### 选项4：Intercept WebSockets Messages
##### 选项5：Response Modification

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.14.png)

##### 选项6：Match and Replace
用于自动替换请求和响应通过代理的部分。对于每一个 HTTP 消息，已启用的匹配和替换规则依次执行，选择适用的规则进行匹配执行。

规则可以分别被定义为请求和响应，对于消息头和身体，并且还特别为只请求的第一行。每个规则可以指定一个文字字符串或正则表达式来匹配，和一个字符串来替换它。对于邮件头，如果匹配条件，整个头和替换字符串匹配留空，然后头被删除。如果指定一个空的匹配表达式，然后替换字符串将被添加为一个新的头。有可协助常见任务的各种缺省规则 - 这些都是默认为禁用。匹配多行区域，您可以使用标准的正则表达式语法来匹配邮件正文的多行区域。

##### 选项7：SSL Pass Through

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.15.png)

##### 选项8：Miscellaneous

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.16.png)

<h2 id="2">Target 模块（目标模块）</h2>

### Target 功能
目标工具包含了 Site map ，用你的目标应用程序的详细信息。它可以让你定义哪些对象在范围上为你目前的工作，也可以让你手动测试漏洞的过程，Target 分为 Site map 和 Scope 两个选项卡。

#### 选项一、Site map
Site map 会在目标中以树形和表形式显示，并且还可以查看完整的请求和响应。树视图包含内容的分层表示，随着细分为地址、目录、文件和参数化请求的 URL 。您还可以扩大有趣的分支才能看到进一步的细节。如果您选择树的一个或多个部分，在所有子分支所选择的项目和项目都显示在表视图。

该表视图显示有关每个项目（URL ，HTTP 状态代码，网页标题等）的关键细节。您可以根据任意列进行排序表（单击列标题来循环升序排序、降序排序和未排序）。如果您在表中选择一个项目，请求和响应（如适用）该项目显示在请求／响应窗格。这包含了请求和响应的 HTTP 报文的编辑器，提供每封邮件的详细分析。

站点地图汇总所有的信息 BurpSuite 已经收集到的有关申请。这包括：

- 所有这一切都通过代理服务器直接请求的资源。
- 已推断出通过分析响应代理请求的任何物品（前提是你没有禁用被动 Spider ）。
- 内容使用 Spider 或内容发现功能查找。
- 由用户手动添加的任何项目，从其它工具的输出。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.1.png)

这样看起来 Site map 是不是很乱，则可以右击 Add to scope ，然后点击 Filter 勾选 Show only in-scope items ，此时你再回头看 Site map 就只有百度一个地址了。这里 Filter 可以过滤一些参数，Show all 显示全部，Hide all 隐藏所有，如果勾选了表示不过滤。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.2.png)

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.3.png)

选择之后就只剩下一个网址了。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.4.png)

针对地址右击显示当前可以做的一些动作操作等功能。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.5.png)

#### 选项二、Scope
这个主要是配合 Site map 做一些过滤的功能。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.6.png)

已请求在 Site map 中的项目会显示为黑色，尚未被请求的项目显示为灰色。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.7.png)

<h2 id="3">Spider 模块（蜘蛛爬行）</h2>

### 一、简介
Burp Spider 是一个映射 web 应用程序的工具。它使用多种智能技术对一个应用程序的内容和功能进行全面的清查。

Burp Spider 通过跟踪 HTML 和 JavaScript 以及提交的表单中的超链接来映射目标应用程序，它还使用了一些其他的线索，如目录列表、资源类型的注释以及 robots.txt 文件。结果会在站点地图中以树和表的形式显示出来，提供了一个清楚并非常详细的目标应用程序视图。

Burp Spider 能使你清楚地了解到一个 web 应用程序是怎样工作的，让你避免进行大量的手动任务而浪费时间。在跟踪链接、提交表单、精简 HTNL 源代码上，可以快速地确认应用程序的潜在的脆弱功能，还允许你指定特定的漏洞，如 SQL 注入、路径遍历。

### 二、模块介绍
要对应用程序使用 Burp Spider 需要两个简单的步骤：

1. 使用 Burp Proxy 配置为你浏览器的代理服务器，浏览目标应用程序（为了节省时间，你可以关闭代理拦截）。
2. 到站点地图的 “ Target ” 选项上，选中目标应用程序驻留的主机和目录。选择上下文菜单的 “ Spider this host／branc ” 选项。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.1.png)

#### 选项一、Control
用来开始和停止 Burp Spider ，监视它的进度，以及定义 spidering 的范围。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.2.png)

#### 选项二、Options
这个选项里包含了许多控制 Burp Spider 动作的选项。

1、Crawler Settings

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.3.png)

- Check robots.txt ：检测 robots.txt 文件，选择后 Burp Spider 会要求和处理 robots.txt 文件，提取内容链接。
- Detect custom "not found" responses ：检测自定义的 "not found" 响应。打开后 Burp Spider 会从每个域请求不存在的资源，编制指纹与诊断 "not found" 响应其它请求检测自定义 "not found" 的响应。
- Ignore links to non-text content ：忽略非文本内容的连接。这个选项被选中，Spider 不会请求非文本资源。使用这个选项，会减少 spidering 时间。
- Request the root of all directories ：请求所有的根目录。如果这个选项被选中，Burp Spider 会请求所有已确认的目标范围内的 web 目录，如果在这个目标站点存在目录遍历，这选项将是非常的有用。
- Make a non-parameterized request to each dynamic page ：对每个动态页面进行非参数化的请求。如果这个选项被选中，Burp Spider 会对在范围内的所有执行动作的 URL 进行无参数的 GET 请求。如果期待的参数没有被接收，动态页面会有不同的响应，这个选项就能成功地探测出额外的站点内容和功能。
- Maximum link depth ：这是 Burp Suite 在种子 URL 里的浏览 "hops" 的最大数。0 表示让 Burp Suite 只请求种子 URL 。如果指定的数值非常大，将会对范围内的链接进行无限期的有效跟踪。将此选项设置为一个合理的数字可以帮助防止循环 Spider 在某些种类的动态生成的内容。
- Maximum parameterized requests per URL ：该蜘蛛用不同的参数请求相同的基本 URL 的最大数目。将此选项设置为一个合理的数字可以帮助避免爬行 “无限” 的内容。

2、Passive Spidering

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.4.png)

- Passively spider as you browse ：如果这个选项被选中，Burp Suite 会被动地处理所有通过 Burp Proxy 的 HTTP 请求，来确认访问页面上的链接和表格。使用这个选项能让 Burp Spider 建立一个包含应用程序内容的详细画面，甚至此时你仅仅使用浏览器浏览了内容的一个子集，因为所有被访问内容链接到内容都会自动地添加到 Suite 的站点地图上。
- Link depth to associate with Proxy requests ：这个选项控制着与通过 Burp Proxy 访问的 web 页面有关的 "link depth" 。为了防止 Burp Spider 跟踪这个页面里的所有链接，要设置一个比上面选项卡里的 "Maximum link depth" 值还高的一个值。

3、Form Submission

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.5.png)

- Individuate forms by ：个性化的形式。这个选项是配置个性化的标准（执行 URL 、方法、区域、值）。当 Burp Spider 处理这些表格时，它会检查这些标准以确认表格是否是新的。旧的表格不会加入到提交序列。
- Don’t submit forms ：开启后蜘蛛不会提交任何表单。
- Prompt for guidance ：提醒向导。如果被选中，在你提交每一个确认的表单前，Burp Suite 都会为你指示引导。这允许你根据需要在输入域中填写自定义的数据，以及选项提交到服务器的哪一个区域。
- Automatically submit using the following rules to assign text field values ：自动提交。如果选中，Burp Spider 通过使用定义的规则来填写输入域的文本值来自动地提交范围内的表单。每一条规则让你指定一个简单的文本或者正则表达式来匹配表单字段名，并提交那些表单名匹配的字段值。
- Set unmatched fields to ：设置不匹配的字段。

4、Application Login

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.6.png)

- Don't submit login forms ：不提交登录表单。开启后 Burp 不会提交登录表单。
- Prompt for guidance ：提示向导。Burp 能交互地为你提示引导。默认设置项。
- Handle as ordinary forms ：以一般形式处理。Burp 通过你配置的信息和自动填充规则，用处理其他表单的方式来处理登陆表单。
- Automatically submit these credentials ：自动提交自定义的数据。开启后 Burp 遇到登录表单会按照设定的值进行提交。

5、Spider Engine

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.7.png)

- Number of threads ：设置请求线程。控制并发请求数。
- Number of retries on network failure ：如果出现连接错误或其他网络问题，Burp 会放弃和移动之前重试的请求指定的次数。测试时，间歇性网络故障是常见的，所以最好是在发生故障时重试该请求了好几次。
- Pause before retry（milliseconds）：当重试失败的请求，Burp 会等待指定的时间（以毫秒为单位）以下，然后重试失败。如果服务器宕机、繁忙或间歇性的问题发生，最好是等待很短的时间，然后重试。
- Throttle between requests（milliseconds）：在每次请求之前等待一个指定的延迟（以毫秒为单位）。此选项很有用，以避免超载应用程序，或者是更隐蔽。
- Add random variations to throttle ：添加随机的变化到请求中。增加隐蔽性。

6、Request Headers
您可以配置头蜘蛛在请求中使用的自定义列表。这可能是有用的，以满足各个应用程序的特定要求。例如，测试设计用于移动设备的应用程序时，以模拟预期的用户代理。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.8.png)

- Use HTTP version 1.1 ：在蜘蛛请求中使用 HTTP／1.1 ，不选中则使用 HTTP/1.0 。
- Use Referer header ：当从一个页面访问另一个页面是加入 Referer 头，这将更加相似与浏览器访问。

<h2 id="4">Scanner 模块（漏洞扫描）</h2>

### 一、简介
Burp Scanner 是一个进行自动发现 web 应用程序的安全漏洞的工具。它是为渗透测试人员设计的，并且它和你现有的手动执行进行的 web 应用程序半自动渗透测试的技术方法很相似。

使用的大多数的 web 扫描器都是单独运行的：你提供了一个开始 URL ，单击“ go ”，然后注视着进度条的更新直到扫描结束，最后产生一个报告。Burp Scanner 和这完全不同，在攻击一个应用程序时它和你执行的操作紧紧的结合在一起。让你细微控制着每一个扫描的请求，并直接反馈回结果。

Burp Scanner 可以执行两种扫描类型：主动扫描（ Active scanning ）、被动扫描（ Passive scanning ）。

### 二、模块说明
#### 1、Issue activity

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.1.png)

#### 2、Scan queue
扫描队列，这里将显示扫描队列的状态进度结果等。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.2.png)

主要包含以下内容：

1. 索引号的项目，反映该项目的添加顺序。
2. 目的地协议，主机和 URL 。
3. 该项目的当前状态，包括完成百分比。
4. 项目扫描问题的数量（这是根据所附的最严重问题的重要性和彩色化）。
5. 在扫描项目的请求数量进行。
6. 网络错误的数目遇到的问题。
7. 为项目创建的插入点的数量。

#### 3、Live scanning
实时扫描可让您决定哪些内容通过使用浏览器的目标应用，通过 BurpProxy 服务器进行扫描。您可以实时主动扫描设定 Live Active Scanning（积极扫描）和 Live Passive Scanning（被动扫描）两种扫描模式。

Live Active Scanning：积极扫描。当浏览时自动发送漏洞利用代码。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.3.png)

Live Passive Scanning：被动扫描。只分析流量不发送任何请求。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.4.png)

#### 4、Issue definitions
漏洞列表，列出了 Burp 可以扫描到的漏洞详情。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.5.png)

#### 5、Options
包含 Burp 扫描选项进行攻击的插入点、主动扫描引擎、主动扫描优化、主动扫描区和被动扫描区域。

##### 1、Attack Insertion Points

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.6.png)

##### 2、Active Scanning Engine

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.7.png)

##### 3、Active Scanning Optimization

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.8.png)

##### 4、Active Scanning Areas

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.9.png)

##### 5、Passive Scanning Areas

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.10.png)

##### 6、Static Code Analysis

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.11.png)

<h2 id="5">Intruder 模块（暴力破解）</h2>

### 一、简介
Burp Intruder 是一个强大的工具，用于自动对 Web 应用程序自定义的攻击，Burp Intruder 是高度可配置的，并被用来在广范围内进行自动化攻击。你可以使用 Burp Intruder 方便地执行许多任务，包括枚举标识符、获取有用数据、漏洞模糊测试。合适的攻击类型取决于应用程序的情况，可能包括：缺陷测试、SQL 注入、跨站点脚本、缓冲区溢出、路径遍历、暴力攻击认证系统、枚举、操纵参数、拖出隐藏的内容和功能、会话令牌测序和会话劫持、数据挖掘、并发攻击和应用层的拒绝服务式攻击。

### 二、模块说明
Burp Intruder 主要有四个模块组成:

1. Target 用于配置目标服务器进行攻击的详细信息。
2. Positions 设置 Payloads 的插入点以及攻击类型（攻击模式）。
3. Payloads 设置 Payload ，配置字典。
4. Opetions 此选项卡包含了 Request Headers 、Request Engine 、Attack Results 、Grep－Match 、Grep－Extrack 、Grep－Payloads 和 Redirections 。你可以在发动攻击之前，在主要 Intruder 的 UI 上编辑这些选项，大部分设置也可以在攻击时对已在运行的窗口进行修改。

#### 1、Target 目标选项（ Target tab ）
这个选项是用来配置目标服务器的细节：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.1.png)

#### 2、Positions 位置选项（ Positions tab ）

这个选项是用来配置在攻击里产生的所有 HTTP 请求的模板：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.2.png)

使用一对`§`字符来标记出有效负荷的位置，在这两个符号之间包含了模板文本的内容。当把一个有效负荷放置到一个给出的请求的特殊位置上时，就把这`§`符号放到这个位置，然后在两个符号之间的出现的文本都会被有效负荷替换。当有个特殊位置没有为一个给出的请求安排有效负荷时（这只适用“ Sniper ”攻击类型），那个位置的`§`字符会被删除，出现在它们之间的文本不会变化。

当使用 Burp Suite 发送一个其他地方的请求时，Burp Intruder 会对你最想放置有效负荷的位置做一个最好的猜测，并且它把这些放置在每个 URL 和主体参数的值里，以及每个 cookie 里。每个标记和它中间的文本都会被加亮以显得更清晰。你可以使用 Intruder 菜单上的选项标记的位置是要替换还是附加现有的参数值。在上面的请求编辑器里，指出了定义位置的数量和文本模板的大小。

你可以使用选项上的按钮来控制位置上的标记：

1. `Add §` — 在当前光标位置插入一个位置标记。
2. `Clear §` — 删除整个模板或选中的部分模板里的位置标记。
3. `Auto §` — 这会对放置标记的位置做一个猜测，放哪里会有用，然后就把标记放到相应位置。这是一个为攻击常规漏洞（ SQL 注入）快速标记出合适位置的有用的功能，然后人工标记是为自定义攻击的。
4. `Refresh` — 如果需要，可以刷新编辑器里有颜色的代码。
5. `Clear` — 删除整个编辑器内容。

#### 3、Payloads 有效负荷选项（Payloads tab）
这个选项是用来配置一个或多个有效负荷的集合。如果定义了“ cluster bomb ”和“ pitchfork ”攻击类型，然后必须为每定义的有效负荷位置（最多 8 个）配置一个单独的有效负荷。使用“ payload set ”下拉菜单选择要配置的有效负荷。

##### 选项1、Payload Sets
Payload数量类型设置

##### 选项2、Payload Opetions［ Simple list ］
该选项会根据选项 1 中 Payload type 的设置而改变

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.3.png)

##### 选项3、Payload Processing
对生成的 Payload 进行编码、加密、截取等操作

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.4.png)

##### 选项4、Payload Encoding
你可以配置哪些有效载荷中的字符应该是 URL 编码的 HTTP 请求中的安全传输。任何已配置的 URL 编码最后应用，任何有效载荷处理规则执行之后。这是推荐使用此设置进行最终 URL 编码，而不是一个有效载荷处理规则，因为可以用来有效载荷的 grep 选项来检查响应为呼应有效载荷的最终 URL 编码应用之前。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.5.png)

#### 4、Opetions 选项卡（ Options tab ）
此选项卡包含了 Request Headers 、Request Engine 、Attack Results 、Grep－Match 、Grep－Extrack 、Grep－Payloads 和 Redirections 。你可以在发动攻击之前，在主要 Intruder 的 UI 上编辑这些选项，大部分设置也可以在攻击时对已在运行的窗口进行修改。

##### 选项1、Request Headers
这些设置控制在 Intruder 中是否更新配置请求头。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.6.png)

如果选中“ Update Content－Length header ”框，Burp Intruder 会使用每个请求的 HTTP 主体长度的正确值，添加或更新这个请求里 HTTP 消息头的内容长度。这个功能对一些需要把可变长度的有效载荷插入到 HTTP 请求模板主体的攻击是很有必要的。这个 HTTP 规范和大多数 web 服务器一样，需要使用消息头内容长度来指定 HTTP 主体长度的正确值。如果没有指定正确值，目标服务器会返回一个错误，也可能返回一个未完成的请求，也可能无限期地等待接收请求里的进一步数据。

如果选中“ Set Connection：close ”框，则 Burp Intruder 会添加或更新 HTTP 消息头的连接来请求在每个请求后已关闭的连接。在多数情况下，这个选项会让攻击执行得更快。

##### 选项2、Request Engine 设置发送请求的线程、超时重试等。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.7.png)

##### 选项3、Attack Results 设置攻击结果的显示。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.8.png)

##### 选项4、Grep－Match 在响应中找出存在指定的内容的一项。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.9.png)

##### 选项5、Grep－Extract 通过正则提取返回信息中的内容。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.10.png)

##### 选项6、Grep－Payloads 这些设置可以用于包含已提交的有效负载的反射的标志结果项目。如果启用了此选项，Burp Suite 会添加包含一个复选框指示当前负载的值在每个响应发现新的结果列。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.11.png)

##### 选项7、Redirections 重定向响应，控制 Burp 在进行攻击时如何处理重定向。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/5.12.png)

<h2 id="6">Repeater 模块（中继器）</h2>

### 一、简介
Burp Repeater 是一个手动修改并补发个别 HTTP 请求，并分析他们的响应的工具。它最大的用途就是和其他 Burp Suite 工具结合起来。你可以从目标站点地图，从 Burp Proxy 浏览记录，或者从 Burp Intruder 攻击结果上的请求，发送到 Repeater 上，并手动调整这个请求来微调对漏洞的探测或攻击。

### 二、模块说明

![](https://github.com/TWater/BurpSuite/raw/master/Picture/6.1.png)

1. 可以从 Proxy history 、Site map 、Scanner 等模块中右键菜单`Send to Repeater`发送到 Repeater ，对页面数据进行修改发送。
2. 点击`go`，发送请求，右边响应请求。
3. 可以通过`<`和`>`来返回上一次和下一个操作。
4. 单击`x`可以删除当前测试请求页面。
5. 底部的功能用于搜索条件，可以用正则表达式，底部右边显示匹配结果数。

`Raw` — 这显示纯文本格式的消息。在文本面板的底部有一个搜索和加亮的功能，可以用来快速地定位出消息里的感兴趣的字符串，如出错消息。搜索栏左边的弹出项让你能控制状况的灵敏度，以及是否使用简单文本或者十六进制搜索。

`Params` — 对于包含参数（ URL 查询字符串、cookie 头，或者消息体）的请求，这个选项把这些参数分析为名字／值的格式，这就可以简单地随他们进行查看和修改了。

`Headers` — 这里是以名字／值的格式来显示 HTTP 的消息头，并且也以原始格式显示了消息体。

`Hex` — 这里允许你直接编辑由原始二进制数据组成的消息。如果在文本编辑器修改某种类型的传输（如：MIME 编码的浏览器请求）可能包含了损坏的二进制内容。为了修改这类消息，应该使用十六进制编辑器。

该模块的设置在菜单栏 Repeater 中，主要选项如下：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/6.2.png)

<h2 id="7">Sequencer 模块（定序器）</h2>

### 一、简介
Burp Sequencer 是一种用于分析数据项的一个样本中的随机性质量的工具。你可以用它来测试应用程序的 session tokens（ 会话 tokens ）或其他重要数据项的本意是不可预测的，比如反弹 CSRF tokens ，密码重置 tokens 等。

### 二、模块说明
Burp Sequencer 主要由三个模块组成：

1. Live capture 信息截取
2. Manual load 手动加载
3. Analysis options 选项分析

#### 1、Live capture 信息截取
##### 选项1、Select Live Capture Request

![](https://github.com/TWater/BurpSuite/raw/master/Picture/7.1.png)

##### 选项2、Token Location Within Response

![](https://github.com/TWater/BurpSuite/raw/master/Picture/7.2.png)

##### 选项3、Live Capture Options

![](https://github.com/TWater/BurpSuite/raw/master/Picture/7.3.png)

#### 2、Manual load 手动加载
##### 选项1、Manual Load

![](https://github.com/TWater/BurpSuite/raw/master/Picture/7.4.png)

#### 3、Analysis options 选项分析
##### 选项1、Token Handling 令牌处理

![](https://github.com/TWater/BurpSuite/raw/master/Picture/7.5.png)

##### 选项2、Token Analysis 令牌分析

![](https://github.com/TWater/BurpSuite/raw/master/Picture/7.6.png)

<h2 id="8">Decoder 模块（编码模块）</h2>

### 一、简介
Burp Decoder 是 Burp Suite 中一款编码解码工具，将原始数据转换成各种编码和哈希表的简单工具，它能够智能地识别多种编码格式采用启发式技术。

### 二、模块说明

![](https://github.com/TWater/BurpSuite/raw/master/Picture/8.1.png)

通过有请求的任意模块的右键菜单 Send to Decoder 或输入数据选择相应的数据格式即可进行解码编码操作，或直接点击 Smart decode 进行智能解码。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/8.2.png)

更重要的是，对于同一个数据，我们可以在 Decoder 的界面，进行多次编码、解码的转换。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/8.3.png)

<h2 id="5">Intruder 模块（暴力破解）</h2>

<h2 id="5">Intruder 模块（暴力破解）</h2>

<h2 id="5">Intruder 模块（暴力破解）</h2>

<h2 id="5">Intruder 模块（暴力破解）</h2>