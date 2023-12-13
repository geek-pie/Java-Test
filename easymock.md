使用 EasyMock 来为 Java 对象自动生成并填充属性通常是不常见的。EasyMock 通常用于模拟(mock)依赖项以进行单元测试。然而，如果你有需要，你可以手动设置模拟对象的行为以返回预设的属性值。

下面是一个简单的例子，展示如何使用 EasyMock 创建 SocialAccount 对象并填充属性：

```java
import org.easymock.EasyMock;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class SocialAccountTest {

    @Test
    public void testSocialAccountCreationAndProperties() {
        // 创建一个 EasyMock 的期望对象
        SocialAccount mockedAccount = EasyMock.createMock(SocialAccount.class);

        // 设置属性值的期望行为
        EasyMock.expect(mockedAccount.getId()).andReturn(123L).anyTimes();
        EasyMock.expect(mockedAccount.getSocialUuid()).andReturn("mockedUuid").anyTimes();
        // 设置其他属性的期望行为 ...

        // 激活 mock 对象
        EasyMock.replay(mockedAccount);

        // 使用预设的值
        assertEquals(123L, mockedAccount.getId());
        assertEquals("mockedUuid", mockedAccount.getSocialUuid());
        // 检查其他属性的值 ...

        // 验证期望的方法是否被调用
        EasyMock.verify(mockedAccount);
    }
}
```

在这个例子中，我们使用 EasyMock 创建了一个 SocialAccount 的模拟对象，并设置了它的属性值的期望行为。然后，我们使用这些预设的属性值，并最终验证了这些方法是否按预期被调用。

需要注意的是，这种方式并不会真正创建一个完整的 SocialAccount 对象，而是创建了一个模拟对象，用于在测试中模拟 SocialAccount 对象的行为以及属性的取值。
