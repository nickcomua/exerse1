<script>
    import { Container, Button, Row, Col } from "sveltestrap";
    let num = 0;
    export let flag = false;
    export let msg = null;
    $: if (flag) {
        add();
        flag = false;
    } 
    let add = () => {
        if (Math.random() >= 0.3) {
            num++;
            msg = [true, "add seccess"];
        }
        else
        {
            msg = [false, "error"]
        }
    };
</script>

<div>
    <Container class="border">
        <Row>
            <Col><h2>hello: {num}</h2></Col>
        </Row>
        <Row>
            <Col>
                <Button
                    on:click={() => {
                        num = 0;
                    }}>clear</Button
                >
            </Col>
            <Col>
                <Button on:click>+</Button>
            </Col>
            <Col><Button on:click={add}>add</Button></Col>
        </Row>
    </Container>
</div>
