## HTTP Lab



##### URI, URL, URN

URI 可以进一步分为定位器、名称，或者二者兼具。术语“Uniform Resource Locator” (URL) 涉及的是 URI 的子集，除识别资源外，它还通过描述其最初访问机制（比如它的网络“位置”）来提供定位资源的方法。 术语“Uniform Resource Name” (URN) 在历史上曾用于引用“urn”方案 [RFC2141] 下的 URI，这个 URI 需要是全球惟一的，并且在资源不存在或不再可用时依然保持不变，对于其他任何拥有名称的一些属性的 URI，都需要使用这样的 URI。

也就是URL和URN是URI的子集。

URI的语法由其scheme决定，“一般URI”包括四个组件，如下：

​	`<scheme>://<authority><path>?<query>` 除了`<sheme>`,其他的组件有可能不存在

1). scheme = alpha *( alpha | digit | "+" | "-" | "." )
2). authority = server | reg_name
3). path = [ abs_path | opaque_part ]
4). query = *uric （字符串信息）

absoluteURI = scheme ":" ( hier_part | opaque_part )

hier_part是指需要有分隔符对不同等级的组件进行分割，opaque_part指不需要有分隔符对不同组件进行分割。

hier_part = ( net_path | abs_path ) [ "?" query ]
net_path = "//" authority [ abs_path ]
abs_path = "/" path_segments
opaque_part = uric_no_slash *uric
uric_no_slash = unreserved | escaped | ";" | "?" | ":" | "@" | "&" | "=" | "+" | "$" | "
relativeURI = ( net_path | abs_path | rel_path ) [ "?" query ]

而URL则通过描述是哪个主机上哪个路径上的文件来唯一确定一个资源，也就是定位的方式来实现的URI。

**locators are also identifiers**, so every URL is also a URI, but there are URIs which are not URLs.

![HTTPLabTCPsegment](../../../Assets/wireshakeLab/HTTPLabTCPsegment.png)



















