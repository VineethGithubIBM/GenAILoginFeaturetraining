# SG Framework Login Functionality



### 1. Feature File for Login with different users
---
---

Feature: Login with different users & register and add bank evidence for Prospect person.

  Scenario Outline: Login with different users.
    Given I login to spm as "<users>"
    And I am on the Home page of the IBM SPM

    Examples:
      | users    |
      | admin    |
      | sysadmin |




### 2. Methods under LoginPageSteps class
---
---
Below is the LoginPageSteps class :-
```
package gov.scot.steps.spm.common;

import gov.scot.pages.spm.common.LoginPage;
import gov.scot.pages.spm.common.SPMBasePage;
import gov.scot.utilities.common.Constants;
import gov.scot.utilities.common.DBUtil;
import gov.scot.utilities.common.UserInterrupt;
import io.cucumber.java.en.And;
import io.cucumber.java.en.Given;
import io.cucumber.java.en.When;

public class LoginPageSteps extends SPMBasePage {

    public LoginPage loginPage;
    public UserInterrupt userInterrupt;

    @Given("^I ask for user input$")
    public void i_ask_for_user_input() throws Exception {
        //todo: add logic so that it is called only when run from local
        // maybe tag based, not call when from jenkins
        sharedData.ADpassword = userInterrupt.askForUserADPassword(getDriver());
    }

    //Given I login to spm as <users>
   //Login with different users
    @Given("^I login to spm as \"([^\"]*)\"$")
    public void i_login_to_spm(String username) throws Exception {
        navigateToSPMUrl();
        waitForPageLoading();
        switch (username) {
            case "bsgcaseworker1":
                sharedData.username = Constants.bsgcaseworker1;
                loginPage.setSpmLoginUsername(Constants.bsgcaseworker1);
                break;
            case "bsgcaseworker2":
                sharedData.username = Constants.bsgcaseworker2;
                loginPage.setSpmLoginUsername(Constants.bsgcaseworker2);
                break;
            case "bsgcaseworker3":
                sharedData.username = Constants.bsgcaseworker3;
                loginPage.setSpmLoginUsername(Constants.bsgcaseworker3);
                break;
            case "bsgsupervisor":
                sharedData.username = Constants.bsgsupervisor;
                loginPage.setSpmLoginUsername(Constants.bsgsupervisor);
                break;
            case "bsgsupervisor1":
            case "Release Supervisor":
                sharedData.username = Constants.bsgsupervisor1;
                loginPage.setSpmLoginUsername(Constants.bsgsupervisor1);
                break;
            case "casclientadvisor":
                sharedData.username = Constants.casclientadvisor;
                loginPage.setSpmLoginUsername(Constants.casclientadvisor);
                break;
            case "casteammanager":
                sharedData.username = Constants.casteammanager;
                loginPage.setSpmLoginUsername(Constants.casteammanager);
                break;
            case "clientexperienceadvisor":
                sharedData.username = Constants.clientexperienceadvisor;
                loginPage.setSpmLoginUsername(Constants.clientexperienceadvisor);
                break;
            case "clientexperienceofficer":
                sharedData.username = Constants.clientexperienceofficer;
                loginPage.setSpmLoginUsername(Constants.clientexperienceofficer);
                break;
            case "admin":
                sharedData.username = "admin";
                loginPage.setSpmLoginUsername("admin");
                break;
            case "sysadmin":
                sharedData.username = "sysadmin";
                loginPage.setSpmLoginUsername("sysadmin");
                break;
            case "feacaseworker1":
                sharedData.username = Constants.feacaseworker1;
                loginPage.setSpmLoginUsername(Constants.feacaseworker1);
                break;
            case "feacaseworker2":
                sharedData.username = Constants.feacaseworker2;
                loginPage.setSpmLoginUsername(Constants.feacaseworker2);
                break;
            case "fspcaseworker3":
                sharedData.username = Constants.fspcaseworker3;
                loginPage.setSpmLoginUsername(Constants.fspcaseworker3);
                break;
            case "fspcaseadvisor":
                sharedData.username = Constants.fspcaseadvisor;
                loginPage.setSpmLoginUsername(Constants.fspcaseadvisor);
                break;
            case "ycgcaseworker1":
                sharedData.username = Constants.ycgcaseworker1;
                loginPage.setSpmLoginUsername(Constants.ycgcaseworker1);
                break;
            case "ycgcaseworker2":
                sharedData.username = Constants.ycgcaseworker2;
                loginPage.setSpmLoginUsername(Constants.ycgcaseworker2);
                break;
            case "feateammanager1":
                sharedData.username = Constants.feateammanager1;
                loginPage.setSpmLoginUsername(Constants.feateammanager1);
                break;
            case "feateammanager2":
                sharedData.username = Constants.feateammanager2;
                loginPage.setSpmLoginUsername(Constants.feateammanager2);
                break;
            case "fspteammanager3":
                sharedData.username = Constants.fspteammanager3;
                loginPage.setSpmLoginUsername(Constants.fspteammanager3);
                break;
            case "jspcaseworker1":
                sharedData.username = Constants.jspcaseworker1;
                loginPage.setSpmLoginUsername(Constants.jspcaseworker1);
                break;
            case "jspmanager1":
                sharedData.username = Constants.jspmanager1;
                loginPage.setSpmLoginUsername(Constants.jspmanager1);
                break;
            case "libfinanceadvisor":
                sharedData.username = Constants.libfinanceadvisor;
                loginPage.setSpmLoginUsername(Constants.libfinanceadvisor);
                break;
            case "libfinancesupervisor":
                sharedData.username = Constants.libfinancesupervisor;
                loginPage.setSpmLoginUsername(Constants.libfinancesupervisor);
                break;
            case "localDeliveryAdvisor":
                sharedData.username = Constants.localDeliveryAdvisor;
                loginPage.setSpmLoginUsername(Constants.localDeliveryAdvisor);
                break;
            case "localDeliverySupervisor":
                sharedData.username = Constants.localDeliverySupervisor;
                loginPage.setSpmLoginUsername(Constants.localDeliverySupervisor);
                break;
            case "mappaAdvisor":
                sharedData.username = Constants.mappaAdvisor;
                loginPage.setSpmLoginUsername(Constants.mappaAdvisor);
                break;
            case "mappaSupervisor":
                sharedData.username = Constants.mappaSupervisor;
                loginPage.setSpmLoginUsername(Constants.mappaSupervisor);
                break;
            case "unacceptableActionAdvisor":
                sharedData.username = Constants.unacceptableActionAdvisor;
                loginPage.setSpmLoginUsername(Constants.unacceptableActionAdvisor);
                break;
            case "unacceptableActionSupervisor":
                sharedData.username = Constants.unacceptableActionSupervisor;
                loginPage.setSpmLoginUsername(Constants.unacceptableActionSupervisor);
                break;
            case "cdpcaseworker":
                sharedData.username = Constants.cdpcaseworker;
                loginPage.setSpmLoginUsername(Constants.cdpcaseworker);
                break;
            case "challengeCEAdvisor":
                sharedData.username = Constants.challengeCEAdvisor ;
                loginPage.setSpmLoginUsername(Constants.challengeCEAdvisor);
                break;
            case "challengecaseofficer":
                sharedData.username = Constants.challengecaseofficer;
                loginPage.setSpmLoginUsername(Constants.challengecaseofficer);
                break;
            case "cdpsupervisor":
                sharedData.username = Constants.cdpsupervisor;
                loginPage.setSpmLoginUsername(Constants.cdpsupervisor);
                break;
            case "adpcaseworker2":
                sharedData.username = Constants.adpcaseworker2;
                loginPage.setSpmLoginUsername(Constants.adpcaseworker2);
                break;
            case "adpsupervisor2":
                sharedData.username = Constants.adpsupervisor2;
                loginPage.setSpmLoginUsername(Constants.adpsupervisor2);
                break;

            /// TEST RUN New User for SI


            case "PTATSI2Casewoker":
                sharedData.username = Constants.PTATSI2Casewoker;
                loginPage.setSpmLoginUsername(Constants.PTATSI2Casewoker);
                break;
            case "PTATSISupervisor2":
                sharedData.username = Constants.PTATSISupervisor2;
                loginPage.setSpmLoginUsername(Constants.PTATSISupervisor2);
                break;



            case "cdpcaseworker1":
                sharedData.username = Constants.cdpcaseworker1;
                loginPage.setSpmLoginUsername(Constants.cdpcaseworker1);
                break;
            case "cdpcaseworker2":
                sharedData.username = Constants.cdpcaseworker2;
                loginPage.setSpmLoginUsername(Constants.cdpcaseworker2);
                break;
            case "cdpcaseworker3":
                sharedData.username = Constants.cdpcaseworker3;
                loginPage.setSpmLoginUsername(Constants.cdpcaseworker3);
                break;
            case "cdpcaseworker4":
                sharedData.username = Constants.cdpcaseworker4;
                loginPage.setSpmLoginUsername(Constants.cdpcaseworker4);
                break;
            case "cdpcaseworker5":
                sharedData.username = Constants.cdpcaseworker5;
                loginPage.setSpmLoginUsername(Constants.cdpcaseworker5);
                break;
            case "cdpsupervisor1":
                sharedData.username = Constants.cdpsupervisor1;
                loginPage.setSpmLoginUsername(Constants.cdpsupervisor1);
                break;
            case "cdpsupervisor2":
                sharedData.username = Constants.cdpsupervisor2;
                loginPage.setSpmLoginUsername(Constants.cdpsupervisor2);
                break;
            case "cdpsupervisor3":
                sharedData.username = Constants.cdpsupervisor3;
                loginPage.setSpmLoginUsername(Constants.cdpsupervisor3);
                break;
            case "cdpsupervisor5":
                sharedData.username = Constants.cdpsupervisor5;
                loginPage.setSpmLoginUsername(Constants.cdpsupervisor5);
                break;
            case "scanningmanager":
                sharedData.username = Constants.scanningmanager;
                loginPage.setSpmLoginUsername(Constants.scanningmanager);
                break;
            case "cwhasupervisor":
                sharedData.username = Constants.cwhasupervisor;
                loginPage.setSpmLoginUsername(Constants.cwhasupervisor);
                break;
            case "cdpScanningManager":
                sharedData.username = Constants.cdpScanningManager;
                loginPage.setSpmLoginUsername(Constants.cdpScanningManager);
                break;
            case "cwhaclientxxpirenceofficer":
                sharedData.username = Constants.cwhaclientxxpirenceofficer;
                loginPage.setSpmLoginUsername(Constants.cwhaclientxxpirenceofficer);
                break;
            case "cwhacaseworker":
                sharedData.username = Constants.cwhacaseworker;
                loginPage.setSpmLoginUsername(Constants.cwhacaseworker);
                break;
            case "debtadvisor":
                sharedData.username = Constants.debtadvisor;
                loginPage.setSpmLoginUsername(Constants.debtadvisor);
                break;
            case "debtsupervisor":
                sharedData.username = Constants.debtsupervisor;
                loginPage.setSpmLoginUsername(Constants.debtsupervisor);
                break;
            case "cwhasupervisor1":
                sharedData.username = Constants.cwhasupervisor1;
                loginPage.setSpmLoginUsername(Constants.cwhasupervisor1);
                break;
            case "cwhacaseworker1":
                sharedData.username = Constants.cwhacaseworker1;
                loginPage.setSpmLoginUsername(Constants.cwhacaseworker1);
                break;
            case "casetransfercaseworker1":
                sharedData.username = Constants.casetransferworker1;
                loginPage.setSpmLoginUsername(Constants.casetransferworker1);
                break;
            case "cdpReleaseSupervisor":
                sharedData.username = Constants.cdpReleaseSupervisor;
                loginPage.setSpmLoginUsername(Constants.cdpReleaseSupervisor);
                break;
            case "cdpReleaseCaseworker":
                sharedData.username = Constants.cdpReleaseCaseworker;
                loginPage.setSpmLoginUsername(Constants.cdpReleaseCaseworker);
                break;
            case "Auto.Superuser":
                sharedData.username = Constants.releaseSuperuser;
                loginPage.setSpmLoginUsername(Constants.releaseSuperuser);
                break;
            case "releaseFinanceCaseworker":
                sharedData.username = Constants.releaseFinanceCaseworker;
                loginPage.setSpmLoginUsername(Constants.releaseFinanceCaseworker);
                break;
            case "adpcaseworker1":
                sharedData.username = Constants.adpcaseworker1;
                loginPage.setSpmLoginUsername(Constants.adpcaseworker1);
                break;
            case "adpsupervisor":
                sharedData.username = Constants.adpsupervisor;
                loginPage.setSpmLoginUsername(Constants.adpsupervisor);
                break;
            case "cearedeterminationappeal":
                sharedData.username = Constants.cearedeterminationappeal;
                loginPage.setSpmLoginUsername(Constants.cearedeterminationappeal);
                break;
            case "ceoredeterminationappeal":
                sharedData.username = Constants.ceoredeterminationappeal;
                loginPage.setSpmLoginUsername(Constants.ceoredeterminationappeal);
                break;
            case "scpcaseworker1":
                sharedData.username = Constants.scpcaseworker1;
                loginPage.setSpmLoginUsername(Constants.scpcaseworker1);
                break;
            case "consultationsIntegrationManager":
                sharedData.username = Constants.consultationsIntegrationManager;
                loginPage.setSpmLoginUsername(Constants.consultationsIntegrationManager);
                break;
            case "CDPCaseworkerDSP":
                sharedData.username = Constants.CDPCaseworkerDSP;
                loginPage.setSpmLoginUsername(Constants.CDPCaseworkerDSP);
                break;
            case "ADPCaseworkerDSP":
                sharedData.username = Constants.ADPCaseworkerDSP;
                loginPage.setSpmLoginUsername(Constants.ADPCaseworkerDSP);
                break;
            case "cspcaseworker1":
                sharedData.username = Constants.cspcaseworker1;
                loginPage.setSpmLoginUsername(Constants.cspcaseworker1);
                break;
            case "cspsupervisor1":
                sharedData.username = Constants.cspsupervisor1;
                loginPage.setSpmLoginUsername(Constants.cspsupervisor1);
                break;
            case "cspsuper":
                sharedData.username = Constants.cspsuper;
                loginPage.setSpmLoginUsername(Constants.cspsuper);
                break;
            case "financeSupervisor":
                sharedData.username = Constants.financeSupervisor;
                loginPage.setSpmLoginUsername(Constants.financeSupervisor);
                break;
            case "sgdisadvisor":
                sharedData.username = Constants.sgdisadvisor;
                loginPage.setSpmLoginUsername(Constants.sgdisadvisor);
                break;
            case "whpcaseworker":
                sharedData.username = Constants.whpcaseworker;
                loginPage.setSpmLoginUsername(Constants.whpcaseworker);
                break;
            case "whpsupervisor":
                sharedData.username = Constants.whpsupervisor;
                loginPage.setSpmLoginUsername(Constants.whpsupervisor);
                break;
            case "whpsupervisor1":
                sharedData.username = Constants.whpsupervisor1;
                loginPage.setSpmLoginUsername(Constants.whpsupervisor1);
                break;
            case "cspcaseworker":
                sharedData.username = Constants.cspcaseworker;
                loginPage.setSpmLoginUsername(Constants.cspcaseworker);
                break;
            case "disabilitycaseworker":
                sharedData.username = Constants.DSP_SI_SPM_CASEWORKER;
                loginPage.setSpmLoginUsername(Constants.DSP_SI_SPM_CASEWORKER);
                break;
            case "disabilitysupervisor":
                sharedData.username = Constants.DSP_SI_SPM_SUPERVISOR;
                loginPage.setSpmLoginUsername(Constants.DSP_SI_SPM_SUPERVISOR);
                break;
            default:
                sharedData.username = "srobertson";
                loginPage.setSpmLoginUsername("srobertson");
                break;
            case "cdpsuperuser":
                sharedData.username = Constants.cdpsuperuser;
                loginPage.setSpmLoginUsername(Constants.cdpsuperuser);
                break;
            case "cspadvisor":
                sharedData.username = "cspadvisor";
                loginPage.setSpmLoginUsername("cspadvisor");
                break;
        }

        // only for demodata, admin and sysadmin, password is password
        if (sharedData.username.equals("admin") || sharedData.username.equals("sysadmin") ||
                sharedData.username.equals("pjohnson") || sharedData.username.equals("srobertson") || sharedData.username.equals("cspsuper") || sharedData.username.equals("cspadvisor")) {
            loginPage.manageLogin(sharedData.username, "password");
            return;
        } else if (sharedData.username.equals("jsmith") || sharedData.username.equals("mclark") || sharedData.username.equals("bconnelly") || sharedData.username.equals("cmacleod") || sharedData.username.equals("ceofficer")) {

            loginPage.setSpmLoginPassword("password");

        } else if (sharedData.username.equals("owilde") || sharedData.username.equals("ejohns") ||
                sharedData.username.equals("jsmith") || sharedData.username.equals("mclark") ||
                sharedData.username.equals("bconnelly") || sharedData.username.equals("cmacleod") ||
                sharedData.username.equals("ceofficer") ) {

            loginPage.setSpmLoginPassword("password");
        } else if (sharedData.username.equals("mclark1")) {
            loginPage.setSpmLoginPassword("Password123!");
        } else {
            loginPage.setSpmLoginPassword(Constants.password);
        }
        loginPage.setSpmLoginSubmit();
    }

    @And("^I wait for application to be up$")
    public void wait_for_application_to_be_up() throws Exception {
        navigateToSPMUrl();
        loginPage.waitForApplicationToBeUp();

    }

    @Given("^Create all SPM Users$")
    public void creatallSPMUsers() throws Exception {
        loginPage.createSPMUsers();
    }

    @When("^I refresh database$")
    public void irefreshdatabase() throws Exception {
        DBUtil.getInstance().RefreshDB();
    }

}

```



### 3. Methods under HomePageSteps class
---
---
Below is the HomePageSteps class:-
```
package gov.scot.steps.spm.common;

import gov.scot.pages.spm.common.HomePage;
import gov.scot.pages.spm.common.SPMBasePage;
import gov.scot.pages.spm.common.clientoutcome.registration.CuramRegisterProspectPersonPage;
import gov.scot.pages.spm.common.clientoutcome.searches.CuramSearchPersonPage;
import gov.scot.pages.spm.common.person.CuramPersonHomePage;
import gov.scot.pages.spm.crossCutting.application.CuramApplicationChallengePage;
import gov.scot.utilities.common.utilityHelpers.DateHelper;
import io.cucumber.java.en.Given;
import io.cucumber.java.en.Then;
import io.cucumber.java.en.When;

import java.util.List;
import java.util.Map;

import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.Matchers.containsString;

public class HomePageSteps extends SPMBasePage {

    HomePage hmePage;
    CuramSearchPersonPage searchPersonPage;
    CuramRegisterProspectPersonPage prospectPersonPage;
    CuramPersonHomePage personHomePage;
    CuramApplicationChallengePage CuramApplicationChallengePage;

//Login with different users
//And I am on the Home page of the IBM SPM
    @Given("^I am on the Home page of the IBM SPM$")
    public void i_am_on_the_home_page_of_the_ibm_spm() throws Throwable {
        hmePage.switchToDefaultFrame();
        waitForPageLoading();
    }

    @When("^I search for pcc case and open from homepage$")
    public void i_search_for_pcc_case_and_open() throws Throwable {
        hmePage.closeAllOpenTabs();
        CuramApplicationChallengePage.fillApplicationNumber(sharedData.pccCaseNumber);

    }

    @When("^I click on the register a prospect person link$")
    public void i_click_on_the_register_a_prospect_person_link() throws Throwable {
        hmePage.clickClientAndOutcomes();
        hmePage.clickHomePageMenu();

        hmePage.clickRegistrationLink();
        hmePage.clickRegisterProspectPersonLink();
        //clickRegisterProspectPersonLink
    }

    @Then("^I should navigate to the prospect registration page$")
    public void i_should_navigate_to_the_prospect_registration_page() throws Throwable {
        prospectPersonPage.switchToRegisterProspectPersonFrame();
        clickNextButton();

    }

    @Then("^I should navigate back to the prospect registration page$")
    public void i_should_navigate_back_to_the_prospect_registration_page() {
        prospectPersonPage.switchToRegisterProspectPersonFrame();
        //prospectPersonPage.clickNext();
    }

    @When("^I click on \"([^\"]*)\" under \"([^\"]*)\" in Shortcuts$")
    public void i_click_on_sub_menu_under_main_menu_link(String subMenu, String mainMenu) {
        hmePage.clickOnAdminWorkSpace();
        hmePage.closeAllOpenTabs();
        hmePage.clickHomePageMenu();
        hmePage.clickMenuLink(mainMenu, subMenu);
    }

    @Then("spm is checked that it is not timetravelled")
    public void spmIsCheckedThatItIsNotTimetravelled() throws Exception {

        String spmCurrentDate = hmePage.getCurrentDateFromSPM();
        String actualCurrentDate = DateHelper.getCurrentDateInSPMformat();

        logger.info("SPM Date - " + spmCurrentDate + " Actual date - " + actualCurrentDate);
        assertThat(spmCurrentDate, containsString(actualCurrentDate));
    }

    @Then("^I switch to \"([^\"]*)\" tab$")
    public void iSwitchToNamedTab(String tabName) {
        switchToTab(tabName);
    }

    @Then("I update properties in SPM")
    public void iUpdatePropertiesInSPM(List<Map<String, String>> properties) {
        hmePage.setSPMProperties(properties);
    }

    @Then("I search for and verify the following details in the property")
    public void iSearchForAndVerifyTheFollowingDetailsInTheProperty(List<Map<String , String>> details) {
        hmePage.verifyPropertyDetails(details);
    }
}

```


### 4. Methods under BasePageObject class
---
---

Below is the BasePageObject class:-
```
package gov.scot.utilities.common;

import com.github.javafaker.Faker;
import com.squareup.okhttp.OkHttpClient;
import com.squareup.okhttp.Request;
import com.squareup.okhttp.Response;
import gov.scot.utilities.common.utilityHelpers.AssertionHelper;
import gov.scot.utilities.common.utilityHelpers.DataHelper;
import gov.scot.utilities.common.utilityHelpers.LogbackUtils;
import net.serenitybdd.core.Serenity;
import net.serenitybdd.core.pages.PageObject;
import net.serenitybdd.core.pages.WebElementFacade;
import net.serenitybdd.model.environment.ConfiguredEnvironment;
import org.apache.commons.lang3.RandomStringUtils;
import org.apache.pdfbox.pdmodel.PDDocument;
import org.apache.pdfbox.text.PDFTextStripper;
import org.json.JSONException;
import org.junit.Assert;
import org.openqa.selenium.NoSuchElementException;
import org.openqa.selenium.*;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedCondition;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.yaml.snakeyaml.Yaml;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.text.DateFormat;
import java.text.DecimalFormat;
import java.text.SimpleDateFormat;
import java.time.Duration;
import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.time.temporal.TemporalAdjusters;
import java.util.*;
import java.util.concurrent.ThreadLocalRandom;
import java.util.concurrent.atomic.AtomicBoolean;
import java.util.concurrent.atomic.AtomicReference;
import java.util.function.Supplier;

import static java.util.concurrent.TimeUnit.SECONDS;
import static org.assertj.core.api.Assertions.assertThat;
import static org.awaitility.Awaitility.await;
import static org.junit.Assert.fail;


public class BasePageObject extends PageObject {
    static final Logger staticLogger = LoggerFactory.getLogger(BasePageObject.class);
    public static Map<String, String> TestDataReference = new HashMap<>();
    public static List<String> TestDataValues = new ArrayList<>();
    public static String RandomRegisteredUserName;
    public SharedData sharedData;
    protected Logger logger = LoggerFactory.getLogger(getClass());
    String envLogLevel = ConfiguredEnvironment.getEnvironmentVariables().getProperty("logging.logginglevel");

    public BasePageObject() {
        LogbackUtils.setLogLevel("", envLogLevel);
        sharedData = getSharedData();
    }
    Yaml yaml = new Yaml();

    /**
     * gets the customised date, if you want the date in past pass the "-ve" value
     *
     * @param daysToAdd   – the days to add, may be negative
     * @param monthsToAdd – the months to add, may be negative
     * @param yearsToAdd  – the years to add, may be negative
     * @return returns date in dd/MM/YY format
     */
    public static String getDate(long daysToAdd, long monthsToAdd, long yearsToAdd) {
        DateTimeFormatter genericFormatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        return LocalDate.now().plusDays(daysToAdd).plusMonths(monthsToAdd).plusYears(yearsToAdd).format(genericFormatter);
    }

    public static String getRandomDBNumber() {
        int randomNineDigits = ThreadLocalRandom.current().nextInt(100000000, 900000000);
        return String.valueOf(randomNineDigits);
    }

    // for example convert 1000 to 1,000.00 to this pass value2 as ("#,###.00")
    public static String returnGivenFormat(String value1, String value2) {
        DecimalFormat df2 = new DecimalFormat(value2);
        return df2.format(Double.parseDouble(value1.replaceAll(",", "")));
    }

    public static String sumOfStringValues(String[] container) {
        DecimalFormat decimalFormatOfSum = new DecimalFormat("#,##0.00");
        Double sum = 0.00;

        for (String element : container) {
            try {
                double num = Double.parseDouble(element.replaceAll(",", ""));
                sum += num;
            } catch (NumberFormatException e) {
                staticLogger.warn(String.format("Element %s in the array is not an integer", element));
            }
        }

        return decimalFormatOfSum.format(sum);
    }

    public static String diffOfStringValues(String value1, String value2) {
        DecimalFormat decimalFormatOfSubtract = new DecimalFormat("#,##0.00");
        Double diff;

        Double num1 = Double.parseDouble(value1.replaceAll(",", ""));
        Double num2 = Double.parseDouble(value2.replaceAll(",", ""));
        diff = num1 - num2;

        return decimalFormatOfSubtract.format(diff);
    }

    public static String currentDateTime() {
        DateFormat dateFormat = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");
        Calendar cal = Calendar.getInstance();
        return dateFormat.format(cal.getTime());
    }

    public static String RandomDate(String daterange) {
        DateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        //SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
        Calendar currentDateBefore = Calendar.getInstance();
        currentDateBefore.add(Calendar.YEAR, -Integer.parseInt(daterange));
        return dateFormat.format(currentDateBefore.getTime());
    }

    public static String RandomDateInbetween(String datefrom, String dateto) throws Exception {
        SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
        //SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
        Date fromdate = sdf.parse(datefrom);
        Date Todate = sdf.parse(dateto);
        Faker faker = new Faker();
        Date dateofBirthBaby = faker.date().between(fromdate, Todate);
        return sdf.format(dateofBirthBaby);
    }

    public static String getRandomNino() {
        int randomSixDigits = ThreadLocalRandom.current().nextInt(100000, 900000);
        //AT & D stand for Automation Test Data :)
        return RandomStringUtils.random(1, "ABCEGHJS") + "T" + randomSixDigits + "D";
    }

    public static String getRandomPhoneNumber() {
        int randomNineDigits = ThreadLocalRandom.current().nextInt(100000000, 900000000);
        int randomTwoDigits = ThreadLocalRandom.current().nextInt(10, 99);
        String a = Integer.toString(randomNineDigits);
        String b = Integer.toString(randomTwoDigits);
        return a + b;
    }

    public static String getRandomPostCode() {
        String[] postcodes = {"EH3 7AA", "EH30 9PT", "EH13 0LS", "EH5 1JF", "EH9 1UL", "EH11 3ES", "EH9 3AQ", "EH3 7LJ", "EH10 5HX",
                "EH7 6HW", "G13 3AE", "G40 2DL", "G42 8UF", "G33 2JZ", "G11 7LP", "G33 2LL", "G33 3BY",
                "G32 9BE", "AB16 7GN", "AB12 3JQ", "AB22 8FG", "AB25 2BU", "AB12 3JS", "AB11 6JZ", "AB24 5EH",
                "EH26 0AA", "EH26 0AB", "EH13 0LS", "EH26 0AD", "EH26 0AE", "EH26 0AF", "EH26 0AG", "EH26 0AH",
                "G20 0AA", "G20 0AB", "G20 0AD", "G20 0AE", "G22 5AA", "G22 5AB", "G22 5AD", "G22 5AG",
                "AB22 8AA", "AB22 8AB", "AB22 8AE", "AB22 8AF", "AB22 8AG", "AB22 8AH", "AB22 8AJ", "AB22 8AL",
                "AB16 5AF", "AB16 5AG", "AB16 5BB", "AB16 5BD", "AB16 5BL", "AB16 5BN", "AB16 5BP",
                "EH22 1AA", "EH22 1AB", "EH22 1AD", "EH22 1AE", "EH12 0AA", "EH12 0AD", "EH12 0AG",
                "G12 0AA", "G12 0AB", "G12 0AD", "G12 0AE", "G12 0AG", "G12 0AH",};

        String randomPostcode = postcodes[new Random().nextInt(postcodes.length)];
        staticLogger.info("Random Postcode selected - " + randomPostcode);
        return randomPostcode;
    }

    public String generatePortalId() {
        StringBuilder portalId = new StringBuilder();

        String characters = "0123456789abcdefghijklmnopqrstuvwxyz";
        Random random = new Random();

        for (int i = 0; i < 36; i++) {
            if (i == 8 || i == 13 || i == 18 || i == 23) {
                portalId.append('-');
            } else {
                int index = random.nextInt(characters.length());
                portalId.append(characters.charAt(index));
            }
        }
        return String.valueOf(portalId);
    }

    public static String checkIfRandomReturnRandomPostcode(String value) {
        if (DataHelper.checkForRandom(value)) {
            return getRandomPostCode();
        } else return value;
    }

    public static void selectDropdownByValue(WebElement dropDownElement, String value) {
        new Select(dropDownElement).selectByValue(value);
    }

    /**
     * Below method is used by CASE TRANSFER team, it generates a random Bank Account number
     */
    public static String getRandomAccNumber() {
        int randomEightDigits = ThreadLocalRandom.current().nextInt(20000001, 89999999);
        return String.valueOf(randomEightDigits);
    }

    public static String getRandomMATB1() {
        int randomNineDigits = ThreadLocalRandom.current().nextInt(100000000, 900000000);
        return String.valueOf(randomNineDigits);
    }

    public SharedData getSharedData() {
        sharedData = Serenity.sessionVariableCalled("SharedData");
        if (sharedData == null) {
            sharedData = new SharedData();
            Serenity.setSessionVariable("SharedData").to(sharedData);
        }
        return sharedData;
    }



  //Login with different users
  //I am on the Home page of the IBM SPM
  // Related to method - i_am_on_the_home_page_of_the_ibm_spm
    public void switchToDefaultFrame() {
        logger.info("Switching to default frame");
        waitForCondition(() -> {
            getDriver().switchTo().defaultContent();
            return true;
        }, "Failed to switch to the default content in the given time of 30 secs");
        waitForPageLoading();
    }

    /**
     * Below method performs switching to parent frame in the browser
     */
    //From Seleniun methods
    public void switchToParentFrame() {
        logger.info("Switching to parent frame");
        waitForCondition(() -> {
            getDriver().switchTo().parentFrame();
            return true;
        }, "Failed to switch to the parent content in the given time of 30 secs");
        waitForPageLoading();
    }

    /**
     * Below method finds an element by xPath and waits until the element is present in the DOM
     */
    //From Seleniun methods
    // This method has been changed to use the below method that is similiar
    public void waitUntilTheElementIsPresent(String xpath) {
        waitUntilTheElementIsPresent(By.xpath(xpath));
    }

    /**
     * Below method is more-generic and it accepts an object of Type "By" (From Webdriver) as parameter, finds an element and determine its presence
     */
    public void waitUntilTheElementIsPresent(By by) {
        logger.info(String.format("Waiting for element to be present at - %s", by.toString()));
        waitForCondition(ExpectedConditions.presenceOfElementLocated(by));
    }

    /**
     * Below method is similar to the above one. It accepts a xpath as parameter, finds that element and determine its visibility
     */
    //From Seleniun methods
    public void waitUntilTheElementIsVisible(String xpath) {
        waitForCondition(ExpectedConditions.visibilityOfElementLocated(By.xpath(xpath)));
    }

    /**
     * Below method is similar to the above one. It accepts a xpath as parameter, finds that element and determine its visibility
     */
    //From Seleniun methods
    public void waitUntilTheElementIsVisible(By by) {
        waitForCondition(ExpectedConditions.visibilityOfElementLocated(by));
    }

    /**
     * Below method is similar to the above one. It accepts a WebElement as parameter, finds that element and determine its visibility
     */
    //From Seleniun methods
    public void waitUntilTheElementIsVisible(WebElement element) {
        waitForCondition(ExpectedConditions.visibilityOfAllElements(element));
    }

    /**
     * Below method performs explicit wait for an element by Text value
     */
    public void waitUntilTextIsPresent(String text) {
        logger.info(String.format("Waiting for text to be present - %s", text));
        String xpath = String.format("(//*[contains(text(),'%s')])[1]", text);
        waitForCondition(ExpectedConditions.textToBePresentInElementLocated(By.xpath(xpath), text));
    }

    /**
     * This method waits for the WebPage to get fully loaded
     */
    public void waitForPageLoaded() {
        waitForPageLoading();
    }

    /**
     * Below method verifies if a text present or not by its xpath
     */
    public boolean verifyTextPresentByXpath(By element, String text) {
        logger.info(String.format("Verifying %s element has %s text", element, text));
        return getText(element).contains(text);
    }

    /**
     * Below method verifies if a text present or not by its xpath
     */
    public boolean verifyTextPresentByXpath(WebElement element, String text) {
        logger.info(String.format("Verifying %s element has %s text", element, text));
        return getText(element).contains(text);
    }

    /**
     * The below method searches and returns a boolean value based on whether a Text is present or not
     */
    public boolean isTextPresent(String str) {
        waitForPageLoading();
        logger.info(String.format("Checking text is present, expected text:%s", str));
        AtomicBoolean isTextDisplayed = new AtomicBoolean(false);
        waitForCondition(() -> {
            isTextDisplayed.set(getDriver().getPageSource().contains(str));
            return true;
        }, "failed to verify the text on DOM");
        return isTextDisplayed.get();
    }

    /**
     * The below method searches and returns a boolean value based on whether an element is present or not by a given String/text value
     */
    public boolean isElementPresent(String str) {
        return containsElements(By.xpath(str));
    }

    /**
     * Below method finds and returns an asynchronous WebElement by its xpath
     */

    public WebElement getFluentElement(final String xpath) {
        return getElementByXpath(xpath);
    }

    /**
     * Below method finds and returns an element by its xpath
     */
    public WebElement getElementByXpath(String xpath) {
        logger.info("Get element using xpath:" + xpath);
        return getElement(By.xpath(xpath));
    }

    public void waitUntilTheElementIsClickable(String xpath) {
        logger.info("Wait for element to be clickable xpath: " + xpath);
        waitForCondition(ExpectedConditions.elementToBeClickable(By.xpath(xpath)));
    }

    public void waitUntilTheElementIsClickable(By elementBy) {
        logger.info("Waiting for element to be clickable xpath" + elementBy);
        waitForCondition(ExpectedConditions.elementToBeClickable(elementBy));
    }

    public void waitUntilTheElementIsClickable(WebElement element) {
        logger.info("Wait for element to be clickable element: " + element);
        waitForCondition(ExpectedConditions.elementToBeClickable(element));
    }

    public void verifyElementExists(final WebElement el) {
        try {
            await().atMost(10, SECONDS).ignoreExceptions().until(() -> el.isDisplayed() || el.isEnabled());
        } catch (Exception e) {
            Assert.fail("WebElement " + el.toString() + " was not found on page");
        }
    }

    public void verifyElementExists(By el) {
        try {
            await().atMost(10, SECONDS).ignoreExceptions().until(() -> getElement(el).isDisplayed() || getElement(el).isEnabled());
        } catch (Exception e) {
            fail("WebElement " + el.toString() + " was not found on page");
        }
    }




    public void selectDropdownValue(WebElement el, String value) {
        verifyElementExists(el);
        Select dropDown = new Select(el);
        dropDown.selectByVisibleText(value);
    }

    /**
     * waits until the frame is available and switches to it.
     * ƒø
     *
     * @param element frame element to switch
     */
    public void switchToFrame(WebElement element) {
        waitForPageLoading();
        logger.info("switch to frame:" + element.toString());
        waitForCondition(ExpectedConditions.frameToBeAvailableAndSwitchToIt(element));
        waitForPageLoading();
    }

    public void switchToFrame(By elementBy) {
        waitForPageLoading();
        logger.debug("switch to frame:" + elementBy.toString());
        waitForCondition(ExpectedConditions.frameToBeAvailableAndSwitchToIt(elementBy));
        logger.debug("Successfully switching to frame:" + elementBy);
        waitForPageLoading();
    }

    public String getText(WebElement element) {
        logger.debug("Get the text of the element using:" + element);
        scrollElementIntoView(element);
        waitForCondition(ExpectedConditions.visibilityOf(element));
        String[] elementText = new String[1];
        waitForCondition(() -> {
            try {
                elementText[0] = element.getText();
                return true;
            } catch (Exception e) {
                return false;
            }

        }, "failed to get the text from the element");
        logger.debug("Returned the text:" + elementText[0] + " for the element:" + element);
        return elementText[0];

    }

    public String getText(By by) {
        logger.debug("Get the text of the element using:" + by);
        scrollElementIntoView(by);
        waitForCondition(ExpectedConditions.visibilityOfElementLocated(by));
        String[] elementText = new String[1];
        waitForCondition(() -> {
            try {
                elementText[0] = findElement(by).getText();
                return true;
            } catch (Exception e) {
                return false;
            }
        }, "unable to retrieve the text from the element");
        return elementText[0];

    }

    /**
     * gets the text of the element using jquery
     *
     * @param querySelector jquery to find the element
     * @return text of the matching element
     */
    public String getTextUsingJquery(String querySelector) {
        logger.debug("Get text of the element using the jquery selector:" + querySelector);
        waitForPageLoading();
        String query = String.format("$('%1$s')", querySelector.replace("'", "\\'"));
        String isElementDisplayed = String.format("return %1$s.length>0;", query);
        waitForCondition(() -> (boolean) evaluateJavascript(isElementDisplayed), "Failed to find the element using jquery: " + query);
        String queryWithScroll = query + "[0].scrollIntoView();" + "return " + query + ".first().text();";
        logger.debug("Get text of element using jquery:" + queryWithScroll);
        return (String) evaluateJavascript(queryWithScroll);
    }

    public void switchToFrameThenClick(By frameToSwitchFromDefault, By elementToClick) {
        logger.info("switching to new frame from the default frame, Frame:" + frameToSwitchFromDefault + "and click:" + elementToClick);
        switchToFrameFromDefault(frameToSwitchFromDefault);
        click(elementToClick);
    }

    public void switchToFrameFromDefault(WebElement frameToSwitchFromDefault) {
        logger.info("switching to new frame from the default frame, Frame:" + frameToSwitchFromDefault);
        switchToDefaultFrame();
        switchToFrame(frameToSwitchFromDefault);
    }

    public void switchToFrameFromDefault(By frameToSwitchFromDefault) {
        logger.info("switching to new frame from the default frame, Frame:" + frameToSwitchFromDefault);
        switchToDefaultFrame();
        waitForCondition(ExpectedConditions.visibilityOfElementLocated(frameToSwitchFromDefault));
        switchToFrame(frameToSwitchFromDefault);
    }

    /**
     * waits for frame to be available and switch to it
     *
     * @param xpath frame x-path
     */
    public void switchToFrame(String xpath) {
        switchToFrame(By.xpath(xpath));
    }

    public void selectVisibileTextByXPath(String xpath, String value) {
        try {
            new Select(getElement(By.xpath(xpath))).selectByVisibleText(value);
            logger.info("The element with xpath:" + xpath + " is selected with value :" + value);
        } catch (Exception e) {
            Assert.fail("The value: " + value + " could not be selected");
        }
    }

    //    Added By Manali
    public void selectVisibileTextByElement(WebElement element, String value) {
        try {
            Select dropDown = new Select(element);
            dropDown.selectByVisibleText(value);

            System.out.println("The element is selected with value :" + value);
        } catch (Exception e) {
            fail("The value: " + value + " could not be selected");
        }
    }

    public void verifyPageHeader(String textVal) throws Throwable {
        waitForPageLoading();
        shouldContainsToIgnoringCase("page header not matched",By.tagName("h1"),textVal);
    }

    public void selectVisibileTextByElement(WebElement element, int index) throws Exception {
        try {
            Select dropDown = new Select(element);
            dropDown.selectByIndex(index);

            System.out.println("The element is selected with index :" + index);
        } catch (Exception e) {
            throw new Exception("The index: " + index + " could not be selected");
        }
    }

    public void selectByDropdown(By by, String dropdownEntry) {
        Select dropDownElement = new Select(findElement(by));
        dropDownElement.selectByVisibleText(dropdownEntry);
    }

    public void selectVisibileTextByIndex(String xpath, int index) throws Exception {
        try {
            new Select(getDriver().findElement(By.xpath(xpath))).selectByIndex(index);
            System.out.println("The element with xpath: " + xpath + " is selected with value :" + index);
        } catch (Exception e) {
            throw new Exception("The value: " + index + " could not be selected");
        }
    }

    public WebElement getWebElementLinkbyText(String lnkText) {
        logger.info("Getting element by linktext " + lnkText);
        try {
            return getElement(By.linkText(lnkText));
        } catch (Exception e) {
            return getElement(By.partialLinkText(lnkText));
        }
    }

    public String currentDate() {
        DateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Calendar cal = Calendar.getInstance();
        String cal1 = dateFormat.format(cal.getTime());
        logger.info(String.format("Getting current date  as%s", cal1));
        return cal1;
    }

    public String ReturnDate(int months, int weeks, int days) {
        int noOfDays = weeks * 7;
        noOfDays = noOfDays + days;
        DateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Calendar currentDate = Calendar.getInstance();
        currentDate.add(Calendar.MONTH, months);
        currentDate.add(Calendar.DAY_OF_YEAR, noOfDays);
        return dateFormat.format(currentDate.getTime());
    }

    /**
     * This JavaScript injection is used to scroll an element into view
     */
    public void scrollElementIntoView(WebElement objElem) {
        waitForPageLoading();
        logger.debug("Scroll into element view:" + objElem);
        waitForConditionWithoutException(() -> {
            evaluateJavascript("arguments[0].scrollIntoView();", objElem);
            return true;
        }, 5, "");

    }

    /**
     * This JavaScript injection is used to scroll an element into view
     */
    public void scrollElementIntoView(By by) {
        logger.debug("Scroll into element view:" + by);
        waitForPageLoading();
        for (int i = 0; i < 3; i++) {
            try {
                evaluateJavascript("arguments[0].scrollIntoView();", getElement(by));
                break;
            } catch (Exception e) {
                logger.warn("unable to scroll into the element view, retry in progress. Element:" + by);
            }
        }
    }

    /**
     * Scrolls to specified element using JavaScript
     *
     * @param cssSelector Css selector
     */
    public void scrollElementIntoView(String cssSelector) {
        logger.debug("Scroll into element view:" + cssSelector);
        waitForPageLoading();
        waitForConditionWithoutException(() -> {
            evaluateJavascript(String.format("document.querySelector(\"%s\").scrollIntoView();", cssSelector));
            return true;
        }, 10, "unable to scroll into the element view,element:" + cssSelector);

    }

    /**
     * Explicit wait based on JS executor call
     */
    @Deprecated
    public void waitForPageToBeLoaded() {
        waitForPageLoading();
    }

    /**
     * Enters key input in text box
     */

    public void click(WebElement element, String sElementName, int time) {
        if (getDriver().toString().contains("appium")) {
            try {
                waitForElementToLoad(element, sElementName, time);
                element.click();
            } catch (StaleElementReferenceException e) {
                fail("Element " + sElementName
                        + " is not attached to the page document");
            } catch (NoSuchElementException e) {

                fail("Element " + sElementName + " was not found in DOM");
            } catch (Exception e) {

                fail("Some Exception occured while clicking on "
                        + sElementName);
            }
        } else {
            try {
                waitForElementToLoad(element, sElementName, time);
                scrollElementIntoView(element);
                element.click();
            } catch (StaleElementReferenceException e) {
                e.printStackTrace();
                fail("Element " + sElementName
                        + " is not attached to the page document");
            } catch (NoSuchElementException e) {
                e.printStackTrace();
                fail("Element " + sElementName + " was not found in DOM");
            } catch (ElementClickInterceptedException e) {
                click(element);
                e.printStackTrace();
            } catch (Exception e) {
                e.printStackTrace();
                fail("Some Exception occured while clicking on "
                        + sElementName);
            }
        }

        waitForPageToBeLoaded();
    }


    /**
     * Web driver waits for visibility of specified web element for the amount
     * of time specified.
     *
     * @return true or false
     */
    @Deprecated
    public boolean waitForElementToLoad(WebElement element, String sElementName, int waitTime) {
        try {
            WebDriverWait wait = new WebDriverWait(getDriver(), Duration.ofSeconds(waitTime));
            logger.info("Waiting for " + sElementName);
            wait.until(ExpectedConditions.visibilityOf(element));
        } catch (TimeoutException e) {
            fail("Element " + sElementName
                    + " was not visible in time - " + waitTime);
            return false;
        } catch (NoSuchElementException e) {
            fail("Element " + element
                    + "is not attached to the page document");
            return false;
        } catch (Exception e) {
            fail("Unable to find the element " + sElementName);
            logger.info(e.getMessage());
            return false;
        }
        return true;
    }

    /**
     * use this method in case if you find any issues with the click() method
     *
     * @param enterOnElement press enter key on the element
     */
    public void pressEnterOnElement(By enterOnElement) {
        scrollElementIntoView(enterOnElement);
        waitForCondition(() -> {
            findElement(enterOnElement).sendKeys(Keys.ENTER);
            return true;
        }, "Failed to press the enter button on the element:" + enterOnElement);
    }

    public void maximizeWindow() {
        getDriver().manage().window().maximize();
    }

    public void switchWindowByName(String name) {
        waitForPageLoading();
        String currentWindow = getDriver().getWindowHandle();
        Set<String> handles = getDriver().getWindowHandles();
        for (String handle : handles) {
            if (getDriver().switchTo().window(handle).getTitle().equals(name))
                break;
            else
                getDriver().switchTo().window(currentWindow);
        }
    }

    public LocalDate getRelativeDate(String dateOffset) {
        LocalDate relativeDate = LocalDate.now().plusDays(Integer.parseInt(dateOffset));
        logger.info("Relative date:" + relativeDate);
        return relativeDate;
    }

    private void navigateToUrl(String pageName) {
        String url = EnvironmentVariables.getEnvironmentVariable(pageName);
        logger.info("Navigating to URL - " + url);
        waitForConditionWithoutException(() -> {
            maximizeWindow();
            getDriver().manage().deleteAllCookies();
            getDriver().navigate().to(url);
            return true;
        }, 80, "Unable to login into the application URL: " + url);
    }


    public void refreshPage() {
        getDriver().navigate().refresh();
    }

  //Given I login to spm as <users>
   //Login with different users
   //Related to 'i_login_to_spm' method	
    public void navigateToSPMUrl() {
        navigateToUrl(EnvironmentVariables.SPM_PAGE);
    }

    public void postCallToJenkinsBuild() throws IOException {
        OkHttpClient client = new OkHttpClient();
        Request request = new Request.Builder()
                .url("http://orchestrator.scotgov-dt.local:8080/job/run-batch-ssdbpp-test21/buildWithParameters?token=JsFKLmZq267dmD23gkfvyTQByzxfZhgd")
                .addHeader("Authorization", "Basic dGVzdGVyMDE6MTFiN2IzMWU5MTQ3MDlkNGI0MDYyZTZhNTI3YTUwYmMyYw==")
                .addHeader("Host", "orchestrator.scotgov-dt.local:8080")
                .build();

        Response response = client.newCall(request).execute();

        if (response.code() != 201) {
            Assert.fail("Jenkins Build trigger failed");
        }

    }

    public void navigateToAEMUrl() {
        navigateToUrl(EnvironmentVariables.AEM_PAGE);
    }

    public void navigateToAEMThank(String thankYouPath) {

        String AEM_base = EnvironmentVariables.getEnvironmentVariable("aem.thankyou");
        String url = AEM_base + thankYouPath;
        maximizeWindow();
        getDriver().get(url);
    }

    public void navigateToDocUploadUrl() {
        navigateToUrl(EnvironmentVariables.DOC_PAGE);
    }

    public boolean verifyTextPresentInElements(String xpath, String text) throws Exception {
        try {
            List<WebElement> AllElemnts = getDriver().findElements(By.xpath(xpath));
            for (WebElement element : AllElemnts) {
                if (getText(element).equalsIgnoreCase(text)) {
                    logger.info(String.format("Verifying %s text is at %s - text found", text, xpath));
                    return true;
                }
            }
            logger.info(String.format("Verifying %s text is at %s - text not found", text, xpath));
            return false;
        } catch (Exception e) {
            throw new Exception("Unknown exception occured while verifying the title FAIL");
        }
    }

    public String ReturnDateMinus(int months, int weeks, int days) {
        int noOfDays = weeks * 7;
        System.out.println("  NO OF Days : " + noOfDays);
        noOfDays = noOfDays + days;
        DateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Calendar currentDate = Calendar.getInstance();
        currentDate.add(Calendar.MONTH, -months);
        currentDate.add(Calendar.DAY_OF_YEAR, noOfDays);
        String datevalue = dateFormat.format(currentDate.getTime());
        System.out.println(datevalue);
        logger.info(String.format("Getting date minus %s months %s weeks %s days - %s",
                months, weeks, days, datevalue));
        return datevalue;
    }

    public void launchdlaapp() {
        navigateToUrl(EnvironmentVariables.CDP_PAGE);
    }

    /*CDP SRTI */
    public void launchdlasrtapp() {
        navigateToUrl(EnvironmentVariables.CDP_SRTI_PAGE);
    }

    /**
     * Launch PIP application url
     */
    public void launchpip() {
        navigateToUrl(EnvironmentVariables.PIP_PAGE);
    }

    /* PIP SRTI PAGE*/
    public void launchpipsrti() {
        navigateToUrl(EnvironmentVariables.PIP_SRTI_PAGE);
    }

    /**
     * Launch Digital Portal application
     */
    public void launchDigitalPortal() {
        navigateToUrl(EnvironmentVariables.DP_PAGE);
    }

    /**
     * launch Notification Mfiles portal
     */
    public void launchNotificationMfilesPortal() {
        navigateToUrl(EnvironmentVariables.MFILES_PAGE);
    }

    /**
     * Navigates to Insights application
     */
    public void navigateToInsightsPage() {
        navigateToUrl(EnvironmentVariables.INSIGHT_PAGE);
    }

    /**
     * Navigates to Appointment Booking Url
     */
    public void navigateToAppointmentBookingUrl() {
        navigateToUrl(EnvironmentVariables.AB_PAGE);
    }

    public void navigateToManagementToolUrl() {
        navigateToUrl(EnvironmentVariables.MANAGEMENT_TOOL_PAGE);
    }

    /**
     * Switches to a immediate child frame
     */
    public void switchToImmediateChildFrame() {
        logger.info("Switching to parent frame");
        getDriver().switchTo().frame(0);
    }

    /**
     * Navigates to Consultation url
     */
    public void navigateToConsultationUrl() {
        navigateToUrl(EnvironmentVariables.CONSULTATION_PAGE);
    }

    /**
     * Navigates to a Mobile consultation Url
     */
    public void navigateToMobileConsultationUrl() {
        navigateToUrl(EnvironmentVariables.CONSULTATION_MOBILE_PAGE);
    }

    /**
     * Navigates to a Consultation Client Portal URL
     */
    public void navigateToConsultationClientPortalUrl() {
        navigateToUrl(EnvironmentVariables.CONSULTATION_CLIENT_PORTAL);
    }

    /**
     * Navigates to a local Delivery url
     */
    public void navigateToLocalDelivery() {
        navigateToUrl(EnvironmentVariables.LOCAL_DELIVERY);
    }

    /**
     * Navigates to DSP URL
     */
    public void navigateToDspUrl() {
        navigateToUrl(EnvironmentVariables.DSP_PAGE);
    }

    public void navigateToSiDspUrl() {
        navigateToUrl(EnvironmentVariables.SI_DSP_PAGE);
    }

    //PPCM
    public void navigateToPPCMUrl() {
        navigateToUrl(EnvironmentVariables.PPCM_PAGE);
    }

    public void navigateToAuditUrl() {
        navigateToUrl(EnvironmentVariables.AUDIT_PAGE);
    }

    public void navigateToPPCMRaiseIncidentUrl() {
        navigateToUrl(EnvironmentVariables.PPCM_INCIDENT_PAGE);
    }

    /**
     * click on the element using the jQuery Script
     *
     * @param scriptOrCSSSelector Jquery script or pass the css selector/query selector  , basically a css selector inside this => $('css selector')
     */
    public void jQueryClick(String scriptOrCSSSelector) {
        logger.debug("Perform jquery click using cssSelector:" + scriptOrCSSSelector);
        String formattedQuery = scriptOrCSSSelector.startsWith("$") ? scriptOrCSSSelector : String.format("$('%1$s')", scriptOrCSSSelector);
        String elementToClick = String.format("$(function(){%1$s[0].scrollIntoView();%1$s[0].click();})", formattedQuery);
        String isElementDisplayed = String.format("return %1$s.length>0;", formattedQuery);
        logger.info("click on the element: " + elementToClick);
        waitForCondition(() -> {
            try {
                if ((boolean) evaluateJavascript(isElementDisplayed)) {
                    evaluateJavascript(elementToClick);
                    return true;
                }
            } catch (NoSuchWindowException exception) {
                return true;
            } catch (Exception ex) {
                return (ex.toString().contains("Cannot read properties of undefined (reading 'scrollIntoView')"));
            }
            return false;
        }, 45, "Failed to click on the element: " + elementToClick);
        waitForPageLoading();
    }

    /**
     * Performs click using JavaScript
     *
     * @param element Element to click
     */
    public void jsClick(WebElement element) {
        waitForPageLoading();
        logger.debug("perform javascript click using element: " + element.toString());
        waitForCondition(ExpectedConditions.elementToBeClickable(element));
        waitForCondition(() -> {
            try {
                evaluateJavascript("arguments[0].scrollIntoView();arguments[0].focus();arguments[0].click()", element);
            } catch (StaleElementReferenceException s) {
                return false;
            }
            return true;
        }, "Failed to click on element:" + element);
        waitForPageLoading();
    }


    public void jsClick(By by) {
        waitForPageLoading();
        logger.debug("Perform java script  click using By: " + by.toString());
        waitForCondition(ExpectedConditions.elementToBeClickable(by));
        waitForCondition(() -> {
            try {
                evaluateJavascript("arguments[0].scrollIntoView();arguments[0].focus();arguments[0].click()", findElement(by));
            } catch (StaleElementReferenceException s) {
                return false;
            }
            return true;
        }, "Failed to click on element:" + by);
        waitForPageLoading();
    }

    /**
     * Performs click using action class from selenium
     *
     * @param element element to click on
     */
    public void performActionClick(WebElement element) {
        waitForPageLoading();
        logger.debug("Perform click  using actions class on element: " + element.toString());
        waitForCondition(ExpectedConditions.elementToBeClickable(element));
        scrollElementIntoView(element);
        waitForCondition(() -> {
            new Actions(getDriver())
                    .moveToElement(element)
                    .click().build().perform();
            return true;
        }, "Fail to perform click on :" + element);

    }

    /**
     * Performs click using Actions class from selenium
     *
     * @param by Identify element using BY class
     */
    public void performActionClick(By by) {
        logger.debug("Perform click  using actions class on element: " + by.toString());
        scrollElementIntoView(by);
        waitForCondition(() -> {
            WebElement element = (WebElement) waitForCondition(ExpectedConditions.elementToBeClickable(by));
            new Actions(getDriver())
                    .moveToElement(element)
                    .click().build().perform();
            return true;
        }, "Fail to perform click on :" + by);
        waitForPageLoading();

    }

    /**
     * Clicks on the element using By, it handles different exceptions
     *
     * @param by Identify element using BY
     */
    public void click(By by) {
        logger.debug("click on element using By:" + by);
        waitForPageLoading();
        waitForCondition(ExpectedConditions.elementToBeClickable(by));
        waitForCondition(() -> {
            try {
                findElement(by).click();
            } catch (ElementClickInterceptedException e) {
                logger.warn("Retry with java script click");
                jsClick(by);
            } catch (ElementNotInteractableException e) {
                logger.warn("Retry with action class click");
                performActionClick(by);
            } catch (StaleElementReferenceException s) {
                logger.warn("thrown stale element exception retry in progress");
                click(by);
            } catch (Exception e) {
                return false;
            }
            return true;
        }, "Fail to perform click on :" + by);

        waitForPageLoading();

    }

    public void clickOnLinkText(String linkText) {
        logger.debug("click on element using link text:" + linkText);
        click(By.partialLinkText(linkText));
    }

    public WebElement getElement(By by) {
        logger.debug("wait for the element to be visible and return using By:" + by);
        return (WebElement) waitForCondition(ExpectedConditions.visibilityOfElementLocated(by));
    }

    public WebElement findElement(By by) {
        logger.debug("get the element without checking for the visibility By:" + by);
        return getDriver().findElement(by);
    }

    public List<WebElement> findElements(By by) {
        logger.debug("get the matching elements,without waiting for the visibility using By:" + by);
        return getDriver().findElements(by);
    }

    /**
     * Gets the element using the css selector
     * it will wait till the element is visible
     *
     * @param query pass the css selector as string
     * @return webElement
     */
    public WebElement getElement(String query) {
        logger.debug("Get element using jquery:" + query);
        String findElementQuery = String.format("return $('%s:visible')[0];", query);
        String isElementDisplayed = String.format("return $('%s:visible').length>0;", query);
        waitForPageLoading();
        waitForCondition(() -> (boolean) evaluateJavascript(isElementDisplayed), "Failed to get the element, using:" + findElementQuery);
        return (WebElement) evaluateJavascript(findElementQuery);
    }

    /**
     * Gets the element using the css selector
     * it will wait till the element is visible
     *
     * @param querySelector pass the css selector as string
     * @return webElement
     */
    public List<WebElement> getElements(String querySelector) {
        String query = format("return jQuery.find('%s')", querySelector);
        logger.debug("Get elements using jquery:" + query);
        String isElementDisplayed = String.format("return $('%s:visible').length>0;", querySelector);
        waitForPageLoading();
        waitForCondition(() -> (boolean) evaluateJavascript(isElementDisplayed), "Failed to get the element, using:" + query);
        return (List<WebElement>) evaluateJavascript(query);
    }


    /**
     * Gets the list of the web element using By
     * it will wait for at least it contains one element,
     * if no elements are displayed in the given time it will throw exception
     *
     * @param by pass the element identifier using by
     * @return list of WebElements
     */
    public List<WebElement> getElements(By by) {
        logger.debug("wait for the visibility of the elements and return using by:" + by);
        waitForCondition(ExpectedConditions.visibilityOfElementLocated(by));
        return getDriver().findElements(by);
    }

    /**
     * clicks on the passed element, it will try with the selenium click in first attempt.
     * if it fails then it will try the other options like jquery and mouse click
     *
     * @param element element to click on
     */
    public void click(WebElement element) {
        scrollElementIntoView(element);
        logger.debug("Perform click on: " + element.toString());
        waitForCondition(ExpectedConditions.elementToBeClickable(element));
        waitForCondition(() -> {
            try {
                element.click();
            } catch (ElementClickInterceptedException e) {
                jsClick(element);
            } catch (ElementNotInteractableException e) {
                performActionClick(element);
            } catch (Exception e) {
                return false;
            }
            return true;
        }, "Fail to perform click on :" + element);
        waitForPageLoading();
    }

    /**
     * Enter text into the element , using BY class
     * Waits for the element to be visible and then sends the text to the element
     *
     * @param by   pass the BY value
     * @param text text to enter into the text box
     */
    public void enterText(By by, String text) {
        logger.info("Enter value into the textbox:" + by + "value:" + text);
        waitForCondition(() -> {
            WebElement element = findElement(by);
            click(element);
            element.clear();
            element.sendKeys(getNonEmptyValue(text));
            return true;
        }, "Failed to enter the text into the text field" + by + "value:" + text);

    }

    /**
     * Enter the text into the element using jQuery
     * waits for the element to be available and sends the text
     *
     * @param Jquery pass the jQuery to identify the element
     * @param value  value to enter into the text box
     */
    public void enterText(String Jquery, String value) {
        logger.debug("Enter value into the textbox using jquery:" + Jquery + "value:" + value);
        waitForPageLoading();
        String script = String.format("%s.first().val(\"%s\")", Jquery, value);
        logger.info("Enter text using :" + script);
        String waitForElement = String.format(" return %s.length>0", Jquery);
        waitForCondition(() -> (boolean) evaluateJavascript(waitForElement), "Element not visible in the given time" + waitForElement);
        evaluateJavascript(script);
    }

    /**
     * Enter text into the TextBox using the WebElement
     *
     * @param element Text box element
     * @param text    Text to enter into the text box
     */
    public void enterText(WebElement element, String text) {
        logger.debug("Enter value into the textbox:" + element + "value:" + text);
        click(element);
        waitForCondition(() -> {
            element.clear();
            element.sendKeys(getNonEmptyValue(text));
            return true;
        }, "Failed to enter the text into the text field" + element + "value:" + text);

    }

//Login with different users	
//1.Given I login to spm as <users> , 2.And I am on the Home page of the IBM SPM
   // Related to 'i_login_to_spm'& 'i_am_on_the_home_page_of_the_ibm_spm' method
    public void waitForPageLoading() {
        try {
            waitForCondition(() -> (Boolean) evaluateJavascript("return document.readyState=='complete'"),
                    "Page not loaded in the given time, page title:" + getDriver().getTitle());
        } catch (Exception e) {
            logger.warn("Page not loaded in the given time");
        }
    }

    /**
     * waits for the specified condition to be met
     *
     * @param action           pass the expected condition, this should return a boolean value
     * @param timeout          pass the timeout in seconds
     * @param messageOnFailure Message to be displayed on failure
     */
    public void waitForCondition(Supplier<Boolean> action, Integer timeout, String messageOnFailure) {
        String[] stackTrace = new String[1];
        try {
            new WebDriverWait(getDriver(), Duration.ofSeconds(timeout), Duration.ofMillis(3000)).withMessage(messageOnFailure + " StackTrace:" + stackTrace[0])
                    .ignoring(Exception.class)
                    .until((d) -> {
                        try {
                            return action.get();
                        } catch (StaleElementReferenceException s) {
                            if (s.getMessage() != null) stackTrace[0] = s.getMessage();
                            return false;
                        } catch (JSONException e) {
                            return false;
                        } catch (Exception e) {
                            if (e.getMessage() != null) stackTrace[0] = e.getMessage();
                            return false;
                        }
                    });
        } catch (Exception e) {
            String strace = stackTrace[0] == null ? "" : stackTrace[0];
            if (!strace.contains("characters read:")) {
                Serenity.takeScreenshot();
                Assert.fail("Message:" + messageOnFailure + "\n" + strace);
            }
        }
    }

    /**
     * waits for the expected condition to be met, default timeout is 30 seconds
     *
     * @param expectedConditions expected condition , supports all the selenium expected conditional options
     * @return object it can be of web element / list of web elements
     */
    public Object waitForCondition(ExpectedCondition expectedConditions) {
        try {
            return new WebDriverWait(getDriver(), Duration.ofSeconds(30)).withMessage("Given condition not met , ExceptedCondition:" + expectedConditions.toString())
                    .ignoring(Exception.class)
                    .until(expectedConditions);
        } catch (Exception e) {
            String strace = e.getMessage() == null ? "" : e.getMessage();
            if (!strace.contains("characters read:")) {
                Serenity.takeScreenshot();
                Assert.fail("Message:" + "\n" + strace);
            }
        }
        return new Object();
    }

    /**
     * Waits for the specific condition to be met.
     * Default timeout is 30 seconds
     * @param action           pass the expected condition , it should return a boolean value
     * @param messageOnFailure Message to be displayed on failure of this condition
     */
    public void waitForCondition(Supplier<Boolean> action, String messageOnFailure) {
        waitForCondition(action, 120, messageOnFailure);
    }

    /**
     * Waits for the specified condition to be met, it won't through any exception on condition fail
     * Exception is muted , it continues after the timeout without exception
     *
     * @param action           condition to met, it should return boolean
     * @param timeoutInSeconds          retry for specified seconds
     * @param messageOnFailure Message to be displayed on condition fail
     */
    public void waitForConditionWithoutException(Supplier<Boolean> action, Integer timeoutInSeconds, String messageOnFailure) {
        try {
            new WebDriverWait(getDriver(), Duration.ofSeconds(timeoutInSeconds), Duration.ofMillis(3000)).withMessage(messageOnFailure + " StackTrace:")
                    .ignoring(Exception.class)
                    .until((d) -> action.get());
        } catch (Exception e) {
            logger.warn("caught with exception, exception muted:" + e.getMessage());
        }
    }

    /**
     * Checks for the existence of the element on the page, if the element exist it returns true
     *
     * @param cssSelector identifies the element using the css selector
     * @return if the element exists it returns true else false
     */
    public boolean containsElements(String cssSelector) {
        waitForPageLoading();
        logger.debug("Checking contains element on the page, element: " + cssSelector);
        String querySelector = cssSelector.startsWith("$") ? cssSelector : format("$(\"%s\")", cssSelector);
        String queryToCheckStatus = String.format("return %1$s.is(':visible');", querySelector);
        boolean status = (boolean) executeJavascript(queryToCheckStatus);
        logger.debug("Is any elements appearing on the page with the Css selector: " + querySelector + " : " + status);
        return status;
    }

    /**
     * Executes the provided JavaScript code using the underlying JavaScript execution engine.
     * The method attempts to execute the code up to 5 times, in case of exceptions, before giving up.
     *
     * @param script The JavaScript code to be executed.
     * @return The result of the JavaScript execution, which can be of any Object type.
     */
    public Object executeJavascript(final String script) {
        for (int i = 0; i < 5; i++) {
            try {
                return evaluateJavascript(script);
            } catch (Exception e) {
                logger.warn("JavaScript execution failed: " + e.getMessage());
            }
        }
        return evaluateJavascript(script);
    }


    /**
     * gets the text of all the elements ,if no elements present, it will throw exception
     *
     * @param cssSelector identifies the element using the css selector
     * @return returns the text of the matched elements
     */
    public List<String> getTextOfAllElements(String cssSelector) {
        String formattedSelector = cssEscape(cssSelector);
        logger.debug("Get the text of all the matching elements using cssSelector:" + cssSelector);
        waitForCondition(() -> containsElements(formattedSelector), "No elements exist");
        String scriptToGetALlElements = String.format("var elements =jQuery.find(\"%s\");var r=[];elements.forEach(e=>r.push(e.textContent.trim()));return r;", formattedSelector);
        return (List<String>) evaluateJavascript(scriptToGetALlElements);
    }

    /**
     * applies the bulk validation
     * @param resultsToValidate
     * @param validationName
     * @throws Exception
     */
    public void applyValidation(Map<String, String> resultsToValidate, String validationName) throws Exception {
        AssertionHelper assertionHelper = new AssertionHelper(validationName);
        for (Map.Entry<String, String> itemToValidate : resultsToValidate.entrySet()) {
            assertionHelper.assertContains(itemToValidate.getKey(), itemToValidate.getKey(), itemToValidate.getValue());
        }
        assertionHelper.displayResultsWithExceptions();
    }

    /**
     * Gets the attribute of the element using By class
     *
     * @param by        how to identify the element
     * @param attribute attribute value
     * @return returns the attribute value
     */
    public String getAttribute(By by, String attribute) {
        logger.debug("Get the attribute of the element:" + by + " attribute:" + attribute);
        AtomicReference<String> attributeValue = new AtomicReference<>("");
        waitForCondition(() -> {
            attributeValue.set(findElement(by).getAttribute(attribute));
            return true;
        }, "Failed to get the attribute value using By:" + by + " attribute:" + attribute);
        return attributeValue.get();
    }

    /**
     * Gets the attribute of the element using Webelement
     *
     * @param element   WebElement
     * @param attribute Attribute of the element
     * @return returns the attribute value
     */
    public String getAttribute(WebElement element, String attribute) {
        logger.debug("Get the attribute of the element:" + element + " attribute:" + attribute);
        waitForCondition(ExpectedConditions.visibilityOf(element));
        return element.getAttribute(attribute);
    }

    /**
     * Clicks on the element and waits for the specified element to be available
     *
     * @param elementToClick   element to click on
     * @param elementToWaitFor expected element to be visible after the click
     */
    public void clickAndWaitForElement(By elementToClick, By elementToWaitFor) {
        logger.debug("click on element:" + elementToClick + " and wait for element :" + elementToWaitFor);
        waitForCondition(() -> {
            pressEnterOnElement(elementToClick);
            return !findElements(elementToWaitFor).isEmpty();
        }, "element not displayed in the given time");
    }

    public void clickAndWaitForElement(String elementToClickCss, String elementToWaitForCss) {
        logger.debug("click on element:" + elementToClickCss + " and wait for element :" + elementToWaitForCss);
        waitForCondition(() -> {
            getElement(elementToClickCss).sendKeys(Keys.ENTER);
            return containsElements(elementToWaitForCss);
        }, "element not displayed in the given time");
    }


    public void shouldContainText(String reason, By by, String textToValidate) {
        String expectedText = getNonEmptyValue(textToValidate);
        logger.debug("verify field " + by + " contains expected text:" + expectedText);
        AtomicReference<String> actualText= new AtomicReference<>("");
        waitForConditionWithoutException(() -> {
            actualText.set(find(by).getTextContent());
            return actualText.get().replace("\n", "").contains(expectedText);
         //   return actualText.get().replaceAll("\\s+","").contains(expectedText);
        }, 20, "");
        assertThat(actualText.get().replaceAll("\\s+","")).describedAs(reason + " Actual: '%s', Expected: '%s'", actualText.get(), expectedText).contains(expectedText.replaceAll("\\s+",""));

    }

    public void shouldBeEqualToText(String reason, By by, String textToValidate) {
        String expectedText = getNonEmptyValue(textToValidate);
        logger.debug("verify field " + by + " shouldBeEqualTo expected text:" + expectedText);
        waitForConditionWithoutException(() -> findElement(by).getText().contains(expectedText), 20, "");
        String actualText = getText(by).replace("\n", "");
        assertThat(actualText).describedAs(reason + " Actual: '%s', Expected: '%s'", actualText, expectedText).isEqualTo(expectedText);

    }

    /**
     * Verifies that the text of the element located by the given 'By' object is equal to the expected text,
     * ignoring the case.
     *
     * @param reason         A reason or description for the validation.
     * @param by             The 'By' object representing the locator of the element to be validated.
     * @param textToValidate The expected text that the element should contain (case-insensitive).
     */
    public void shouldBeEqualToIgnoringCase(String reason, By by, String textToValidate) {
        String expectedText = getNonEmptyValue(textToValidate);
        logger.debug("Verifying field {} should be equal to text (ignoring case): {}", by, expectedText);

        waitForConditionWithoutException(() -> findElement(by).getText().toLowerCase().contains(expectedText.toLowerCase()), 20, "");
        String actualText = getText(by).replace("\n", "");
        assertThat(actualText).describedAs(reason + " Actual: '%s', Expected: '%s'", actualText, expectedText).isEqualToIgnoringCase(expectedText);
    }

    public void shouldContainsToIgnoringCase(String reason, By by, String textToValidate) {
        String expectedText = getNonEmptyValue(textToValidate);
        logger.debug("Verifying field {} should contain text (ignoring case): {}", by, expectedText);

        waitForConditionWithoutException(() -> findElement(by).getText().toLowerCase().contains(expectedText.toLowerCase()), 20, "");
        String actualText = getText(by).replace("\n", "");
        assertThat(actualText).describedAs(reason + " Actual: '%s', Expected: '%s'", actualText, expectedText).containsIgnoringCase(expectedText);
    }

    /**
     * verifies the value on the text
     *
     * @param reason         message to be displayed on failure
     * @param by             element to check
     * @param textToValidate expected text on the element
     */
    public void shouldContainValue(String reason, By by, String textToValidate) {
        String expectedText = getNonEmptyValue(textToValidate);
        logger.debug("verify field " + by + " shouldContainValue :" + expectedText);
        waitForConditionWithoutException(() -> getAttribute(by, "value").contains(expectedText), 20, "");
        String actualValue = getAttribute(by, "value");
        assertThat(actualValue).describedAs(reason + " Actual: '%s', Expected: '%s'", actualValue, expectedText).contains(expectedText);
    }

    public void waitForSpecificTime(int time) throws InterruptedException {
        Thread.sleep(time);
    }
    /**
     * Returns the text from the specified page in the pdf file
     * @param file pdf file
     * @param pageIndex page index , page1 can be read with index 0
     * @return
     * @throws IOException
     */
    public String getTextFromPDFPage(File file, int pageIndex) throws IOException {
        waitForCondition(file::exists, "File does not exists in the given path:" + file);
        PDFTextStripper stripper = new PDFTextStripper();
        PDDocument document = PDDocument.load(file);
        stripper.setStartPage(pageIndex + 1);
        stripper.setEndPage(pageIndex + 1);
        String extractedText = stripper.getText(document);
        document.close();
        return extractedText;
    }

    /**
     * checks the value is not null or not empty
     *
     * @param value value to check
     * @return returns true if the value is not null or not empty
     */
    public boolean isNotNullOrEmpty(String value) {
        return !isNullOrEmpty(value);
    }

    /**
     * checks the value is null or empty
     *
     * @param value value to check
     * @return return true if the value is null or empty
     */
    public boolean isNullOrEmpty(String value) {
        return value == null || value.isEmpty();
    }

    /**
     * Returns a formatted string  using the formatted string and arguments
     *
     * @param stringToFormat string to be formatted
     * @param args           arguments to pass to the format
     * @return formatted string
     */
    public String format(String stringToFormat, Object... args) {
        return String.format(stringToFormat, args);
    }

    /**
     * scrolls to the bottom of the page, Note only works on the jquery supported pages only
     */
    public void scrollToPageBottom() {
        waitForConditionWithoutException(() -> {
            evaluateJavascript("$(function(){$('html, body').scrollTop($(document).height());})");
            return true;
        }, 8, "failed to scroll into the bottom of the page");
    }

    /**
     * scrolls to the Top of the page, Note only works on the jquery supported pages only
     */
    public void scrollToPageTop() {
        waitForConditionWithoutException(() -> {
            evaluateJavascript("window.scrollTo(0, 0);");
            return true;
        }, 8, "failed to scroll into the bottom of the page");
    }

    public String cssEscape(String using) {
        return using.replaceAll("(['\"\\\\#.:;,!?+<>=~*^$|%&@`{}\\-\\/\\[\\]\\(\\)])", "\\\\$1");
    }

    /**
     * Returns the specified value if it is not null or empty, or an empty string otherwise.
     *
     * @param value the value to check
     * @return the non-empty value, or an empty string if the value is null or empty
     */
    public String getNonEmptyValue(String value) {
        return isNullOrEmpty(value) ? "" : value;
    }
    /**
     * Purpose: This Common method is to read data form Yaml file for eligibility amount across all benefits
     * Types include:
     *
     * @return
     */

    public String yamlFileReader(String eligibleAmount) {
        String amount;
        try {
            FileInputStream input = new FileInputStream("src/test/resources/testdata/Uprating/upratingData.yaml");
            Map<String, Object> obj = yaml.load(input);
            amount = (String) obj.get(eligibleAmount);
            logger.info(amount);
        } catch (FileNotFoundException ex) {
            throw new RuntimeException(ex);
        }
        return amount;
    }

    /**
     * Formats a date based on the provided time components.
     *
     * @param time A string containing time components such as years, months, weeks, and days.
     *             For example, "2 years 3 months 4 weeks 5 days".
     * @return A formatted date string in the "yyyy-MM-dd" format based on the provided time components.
     * @throws IllegalArgumentException If the input string is not in the expected format or if
     *                                  any component's value is negative.
     */
    public String getDate(String time, String format) {
        int days = 0;
        int years = 0;
        int months = 0;
        int weeks = 0;

        String[] parts = time.split("\\s+");
        for (int i = 0; i < parts.length; i++) {
            String part = parts[i].toLowerCase();
            if (part.contains("day")) {
                days = Integer.parseInt(parts[i - 1]);
            } else if (part.contains("month")) {
                months = Integer.parseInt(parts[i - 1]);
            } else if (part.contains("year")) {
                years = Integer.parseInt(parts[i - 1]);
            } else if (part.contains("week")) {
                weeks = Integer.parseInt(parts[i - 1]);
            }
        }

        DateTimeFormatter genericFormatter = DateTimeFormatter.ofPattern(format);
        LocalDate resultDate = LocalDate.now().plusDays(days).plusMonths(months).plusYears(years).plusWeeks(weeks);
        return resultDate.format(genericFormatter);
    }
    /**
     * Checks an array is in descending order
     *
     * @param array arr to check values are in descending order
     * @return returns true or false depending on if the values are in descending order
     */
    public <T extends Comparable<T>> boolean isSortedDescending(T[] array) {
        for (int i = 1; i < array.length; i++) {
            if (array[i].compareTo(array[i - 1]) > 0) {
                return false;
            }
        }
        return true;
    }
}


```



### 5. Methods under SPMBasePage class
---
---
Below is the SPMBasePage class:-
```
package gov.scot.pages.spm.common;

import gov.scot.utilities.common.BasePageObject;
import gov.scot.utilities.common.utilityHelpers.DateHelper;
import net.serenitybdd.core.Serenity;
import net.serenitybdd.core.pages.WebElementFacade;
import org.assertj.core.api.Assertions;
import org.jetbrains.annotations.NotNull;
import org.junit.Assert;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.FindBy;
import org.yaml.snakeyaml.Yaml;
import org.openqa.selenium.support.ui.ExpectedConditions;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.time.format.DateTimeFormatter;
import java.util.*;
import java.util.concurrent.atomic.AtomicBoolean;
import java.util.function.Supplier;

import static gov.scot.pages.spm.common.SPM.CaseType;
import static gov.scot.utilities.common.utilityHelpers.DataHelper.notEmptyOrNull;
import static org.hamcrest.CoreMatchers.containsString;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.Matchers.equalTo;
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.fail;

public class SPMBasePage extends BasePageObject {

    public By SearchPersonFrame = By.cssSelector("iframe[title='Content Panel - Person Search'][src*='Person_search']");
    @FindBy(xpath = "//a[@title='Click here to submit your answers and display the next page.']")
    public WebElement nextButton;
    public By pageTitleHeading = By.id("pageTitleHeading");
    public By personSearchButton = By.cssSelector("#page-action-set- span.middle");
    public String errorMessageOnModalWindow = "ul[id='error-messages']";
    public By caseEligibilityDecision = By.cssSelector("div[data-testid*='CurrentEligibilityChecks'] tr[data-lix] td:nth-child(3)");
    By applicationCaseEvidenceFrame = By.cssSelector("iframe[title='Content Panel - Evidence'][src*='ApplicationCaseEvidence']");
    By personEvidenceFrame = By.cssSelector("iframe[title^='Content Panel - Evidence'][src*='PDCEvidence']");
    By ShortCutMenuIcon = By.cssSelector("a[aria-label='Shortcuts']");
    By appropriateTabBasedOnRole = By.cssSelector("span[title='Clients and Outcomes'],span[title='Teams and Workload'],span[title='Team and Workloads'],span[title='System Configurations'],span[title='Administration Workspace']");
    By programHeaderFrame = By.xpath("//iframe[contains(@page-id,'CommonIntake_applicationCaseHomeContextPanel') or contains(@page-id,'DefaultICProduct_tabDetails') or contains(@title,'Context Panel - Child Winter Heating Assistance')]");
    By applicationStatus = By.cssSelector("div[class='application-case-status'], div[class='pd-status']");
    public By pdcEvidenceFrame=By.xpath("//iframe[@title='Content Panel - Active Evidence']");

    String script = "document.querySelector('a[title=\"Click here to submit your answers and display the next page.\"]').click();";
    By calendarSpmDate = By.xpath("//*[@title='Go to Date dd/MM/yyyy']");

    By calenderGoTodayButton = By.xpath("//a[text()='Go to Today']");
    By calendarFrame = By.xpath("//iframe[contains(@data-content-url,'CalendarPage')]");
    By calendarView = By.xpath("//*[@title='Calendar View']");
    By inboxShortcutIcon = By.cssSelector("#DefaultAppInboxSection-sbc a[aria-label='Shortcuts'] >img");
    By logoutFinal = By.xpath("//*[text()='Log Out']");
    By activeModalDialogFrame = By.cssSelector("iframe[id*='curam_modal_CuramCarbonModal']");
    By proofsOutstandingErrorMessage = By.xpath("//div[contains(text(),'Proofs outstanding. Mark them as')]");
    public By SearchDocumentFrame = By.cssSelector("iframe[title='Content Panel - Document List']");
    By infoBar = By.xpath("//div[text()='Ready for case manager task has not been created as Part2 is not present']");
    /**
     * switches to the tab that contains the matched text
     *
     * @param textOnTab text on the tab
     */
    public SPMBasePage switchToTabContainsText(String textOnTab) {
        logger.info("Switch to the tab that contains text:" + textOnTab);
        switchToDefaultFrame();
        jQueryClick(String.format("$('*[title*=\"%s\"][role=\"tab\"]')", cssEscape(textOnTab) ));
        return this;
    }

    /**
     * switches to the default frame and clicks on the save button
     */
    public void clickSaveButton() {
        logger.info("switch to default frame and click on save button");
        clickModelButton("Save");
    }

    public void clickCancelButton() {
        logger.info("switch to default frame and click on cancel button");
        clickModelButton("Cancel");
    }

    public void clickSaveButtonIEG() {
        logger.info("switch to default frame and click on save button");
        clickModelButtonIEG("Save");
    }

    public void checkForResolutionElseThrowError() {
        waitForDataDisplay();
        if (!isModalWindowExists()) return;
        switchToActiveModalDialog();
        if (!findElements(By.cssSelector("*[id $='error-messages']")).isEmpty()) {
            String ErrorMessage = getText(By.cssSelector("*[id $='error-messages']"));
            if (ErrorMessage.contains("valid money")) {
                String fieldName = ErrorMessage.split("'")[1];
                for (WebElement element : findElements(By.cssSelector(format("input[title='%1$s']", fieldName)))) {
                    String amount = element.getAttribute("value").split("£")[1];
                    enterText(element, amount);
                }
                clickSaveButton();
            } else if (ErrorMessage.contains("Discrepancies") || ErrorMessage.contains("item")) {
                clickSaveButton();
            }  else if (ErrorMessage.contains("Days late is > 0 late reason must be entered")) {
                selectValueFromDropdown("Reason For Lateness", "Bereavement");
                clickSaveButton();
            } else if (ErrorMessage.contains("cannot be before the current date and current deadline date")) {
                String deadlineDateTT = getSharedData().spmCalendarDate;
                String xpath = "//label[@title='Deadline Date']/../div//input";
                enterText(By.xpath(xpath), deadlineDateTT);
                clickSaveButton();
            } else if (ErrorMessage.contains("Please select the option")) {
                String optionToSelect = ErrorMessage.substring(ErrorMessage.indexOf('\'')+1,ErrorMessage.lastIndexOf('\''));
                clickModelButton("Back");
                switchToFrameByTitle("Verify Evidence");
                selectValueFromDropdown("Item",optionToSelect);
                clickModelButton("Next");
                clickSaveButton();
            } else if (ErrorMessage.contains("assigned to you")) {
                clickCancelButton();
            }
            else {
                Assert.fail(ErrorMessage);
            }
        }
    }

    /**
     * Switches to a new frame that contains the matching title
     * Note: it will switch to default first and then to the new frame
     *
     * @param title frame title
     */
    public void switchToFrameByTitle(String title) {
        logger.info("switch to default frame and then switch to frame:" + title);
        waitForDataDisplay();
        waitForCondition(() -> {
            getDriver().switchTo().defaultContent();
            waitForCondition(ExpectedConditions.frameToBeAvailableAndSwitchToIt(getElement(format("iframe[title *=\"%s\"]", title))));
            return true;
        }, 50, "unable to switch to the frame :" + title);
    }

    /**
     * Switches to a new frame that contains the matching title
     * Note: it will switch from existing frame to the new frame
     *
     * @param title frame title
     */
    public void switchToFrame(String title) {
        logger.debug("switch to new frame from an existing frame:" + title);
        waitForDataDisplay();
        waitForCondition(() -> {
            waitForCondition(ExpectedConditions.frameToBeAvailableAndSwitchToIt(getElement(format("iframe[title *=\"%s\"]", title))));
            return true;
        }, 50, "unable to switch to the frame :" + title);
    }



    /**
     * Enters the value into the text box or textarea  using the field labels
     * For example:
     * enterValueInto("First Name","firstName")
     *
     * @param textBoxLabel name/title of the field  ex: First Name, Reference
     * @param value        value to enter into that text box
     */
    public void enterValueInto(String textBoxLabel, String value) {
        logger.debug("enter the text into the field:" + textBoxLabel);
        waitForDataDisplay();
        By element = By.cssSelector(format("input[title*=\"%1$s\"],input[aria-label*=\"%1$s\"],textarea[title*=\"%1$s\"]", textBoxLabel));
        enterText(element, value);
    }

    /**
     * sets the date into the date fields
     *
     * @param label date field label
     * @param date  date to be entered into the date field
     */
    public void setDateField(String label, String date) {
        logger.info("enter the date value into the date field:" + date);
        setFieldValue(label, date);
    }

     /**
     * Updates a field in the application with the provided value.
     * The method first checks the type of the field based on its label and then performs the update accordingly.
     * If the field is a combobox (drop-down), it selects the specified value from the dropdown options.
     * If the field is a text input, it enters the given value into the text input.
     * If the field is neither a combobox nor a text input, and the provided value is null or empty,
     * it sets the date field to the current date.
     *
     * @param fieldLabel  The label of the field to be updated.
     * @param fieldValue  The value to update the field with. For combobox, it represents the value to select;
     *                    for text input, it is the text to be entered; for other fields, it can be null or empty.
     *
     * @throws NoSuchElementException if the field with the given label is not found in the application.
     * @throws IllegalArgumentException if an invalid field type is encountered or if the provided fieldValue
     *                                  is invalid for the corresponding field type.
     */
    public void updateFieldWithValue(String fieldLabel, String fieldValue) {
        if (containsElements(format("input[title*='%s'][role='combobox']", fieldLabel))) {
            selectValueFromDropdown(fieldLabel, fieldValue);
        } else if (containsElements(format("input[title*='%s'].text", fieldLabel))) {
            enterValueInto(fieldLabel, fieldValue);
        } else {
            if (isNullOrEmpty(fieldValue)) {
                String formatted_date;
                formatted_date = DateHelper.getRelativeDateFromAnyDay(getSharedData().spmCalendarDate, "SPM Calendar Date", "dd/MM/yyyy");
                setDateField(fieldValue, formatted_date);
            }
        }
    }

    /**
     * sets the field value using jquery,
     *
     * @param label field label
     * @param value value to be set into the field
     */
    public void setFieldValue(String label, String value) {
        String query = format(" $('input[aria-label^=\"%1$s\"],input[title*=\"%1$s\"],label:contains(\"%1$s\") +div input')",  cssEscape(label));
        String isElementDisplayed = format("return %1$s.length>0;", query);
        String elementToSetValue = format("$(function(){ %1$s.first().val(\"%2$s\");})", query, value);
        logger.info("click on the element: " + elementToSetValue);
        waitForCondition(() -> {
            if ((boolean) evaluateJavascript(isElementDisplayed)) {
                evaluateJavascript(elementToSetValue);
                return true;
            }
            return false;
        }, "Failed to click on the element: " + script);
    }


    /**
     * Expands the shortcuts menus under specific tab
     * if the short-cuts menu is already expanded it won't do anything.
     * For Example:
     * expandShortCuts("Inbox")
     *
     * @param tab provide the name of the tab section
     */
    public void expandShortCuts(String tab) {
        logger.info("switch to tab :" + tab + " and expand the shortcuts Menu");
        waitForDataDisplay();
        if (tab.equals("Inbox")) {
            waitForCondition(() -> {
                if (getAttribute(By.cssSelector("#DefaultAppInboxSection-sbc a[aria-label='Shortcuts']"), "aria-expanded").equals("false")) {
                    click(inboxShortcutIcon);
                }
                return true;
            }, "failed to expand the shortcuts menu");
        } else {
            waitForCondition(() -> {
                if (getElement(ShortCutMenuIcon).getAttribute("aria-expanded").equals("false")) {
                    click(By.cssSelector("img.shortcutsPanelIcon"));
                }
                return true;
            }, "failed to expand the shortcuts menu");
        }
    }

    /**
     * closes all the tabs that are opened under different sections, ex: client and outcomes , inbox and etc..
     * For Example:
     * closeAllOpenTabs()
     */
    public SPMBasePage closeAllOpenTabs() {
        logger.info("close all open tabs");
        waitForDataDisplay();
        switchToDefaultFrame();
        click(appropriateTabBasedOnRole);
        try {
            evaluateJavascript("document.querySelectorAll(\"button[title^='Close']\").forEach(element => element.click());");
        } catch (Exception e) {
            logger.info("No tabs to close");
        }
        return this;
    }

    /**
     * Switches to new tab in SPM
     * For example:
     * switchToTab("Inbox")
     *
     * @param tabName provide the exact label name on the tab, examples: Inbox, Evidence, Eligibility Checks etc..
     */
    public SPMBasePage switchToTab(String tabName) {
        logger.debug("switch to default frame and click on the tab:" + tabName);
        waitForDataDisplay();
        waitForPageLoading();
        switchToDefaultFrame();
        clickOnTab(tabName);
        return this;
    }

    /**
     * clicks on the tab
     *
     * @param tabName name of the tab
     */
    public void clickOnTab(String tabName) {
        logger.info("click on the tab without switching to default frame Tab Name:" + tabName);
        String script = String.format("$('span[title^=\"%1$s\"][role=\"tab\"]:visible').last()", cssEscape(tabName));
        waitForCondition(() -> {
            jQueryClick(script);
            waitForDataDisplay();
            waitForPageLoading();
            return evaluateJavascript(format("return %1$s.attr(\"aria-selected\")", script)).equals("true");
        }, "Failed to click on the selected tab: " + tabName);
    }

    /**
     * selects the sub tabs under the table,
     *
     * @param childTab tab name to select
     */
    public void selectSubTab(String childTab) {
        logger.info("switch to default frame and select the sub tab or child tab : " + childTab);
        switchToDefaultFrame();
        String script = String.format("$('div[title=\"%1$s\"][role=\"button\"]:visible').last()",cssEscape(childTab));
        waitForCondition(() -> {
            jQueryClick(script);
            return (Boolean) evaluateJavascript(String.format("return $('div[title=\"%1$s\"][role=\"button\"]:visible').last().parent().attr(\"class\").indexOf(\"not-selected\")==-1", childTab));
        }, "Failed to click on the  selected subTab: " + childTab);
        waitForDataDisplay();
    }

    /**
     * closes the tab based on the name, it first switches to a specified section and close the tab under it.
     * For Example:
     * closeTabByName("Client and Outcomes", pdcType)
     *
     * @param section         provide the section name, it's the main toolbar option
     * @param tabContainsText provide the name of the tab to be closed
     */
    public void closeTabByName(String section, String tabContainsText) {
        logger.info("close the open tab that contain text : " + tabContainsText);
        switchToDefaultFrame();
        String tabClosures = "button[title^='Close']";
        if (containsElements(tabClosures)) {
            if (tabContainsText.equals("last")) {
                jQueryClick(format("$('button[title^=\"Close\"]:visible').last()", tabClosures));
                return;
            }
            if (tabContainsText.equals("first")) {
                jQueryClick(format("$('button[title^=\"Close\"]:visible').first()", tabClosures));
                return;
            }
            performActionClick(By.cssSelector(String.format("span[title*='%s'] +button", tabContainsText)));
        }

    }

    /**
     * selects the specified menu option from the left side shortcut menu
     * For Example:
     * selectOptionFromShortcutsMenu("Clients and Outcomes", "Searches", "Person")
     *
     * @param tab            provide the name of the main toolbar tab name
     * @param searchSection  provide the name of the section under which your option exist
     * @param optionToSelect provide the name of the option to select from the shortcut menu
     */
    public void selectOptionFromShortcutsMenu(String tab, String searchSection, String optionToSelect) {
        logger.info("switch to tab " + tab + "and select the section :" + searchSection + " option:" + optionToSelect);
        By shortcutSection = By.cssSelector(String.format("span[title='%s']", searchSection));
        String shortcutOptionBy = format("div[aria-label=\"%1$s\"] a[title^=\"%2$s\"]", cssEscape(searchSection) , cssEscape(optionToSelect) );
        expandShortCuts(tab);
        waitForCondition(() -> {
            click(shortcutSection);//expand section
            if (!Objects.equals(optionToSelect, "")) jQueryClick(shortcutOptionBy);// select option
            return true;
        }, "failed to select the option from shortcuts menu");
        waitForDataDisplay();
    }

    /**
     * searches and selects the person record based on reference , first name , last name
     * if the record doesn't appear in first time then it will re-try for up to 8 mins
     * For Example:
     * selectPersonRecord(getSharedData().nino, "", "")   => search by NINO
     * selectPersonRecord("", "FirstName", "LastName")   => search by first name and last name
     *
     * @param nino             provide NINO, if the value is null or empty it will go by first name and last name
     * @param personFirstName  first name
     * @param personSecondName last or second name
     */
    public void selectPersonRecord(String nino, String personFirstName, String personSecondName) {
        searchPerson(nino, personFirstName, personSecondName);
        jQueryClick("table[summary^=\"Search Results\"] tr[data-lix]  .ac");
        waitForDataDisplay();
        logger.info("Navigate to most recent application");
    }

    /**
     * searches the person record based on NINO , first name , last name, shortAddress
     * For Example:
     * searchPerson(personNino, personFirstName, personSecondName, shortAddress)
     * searchPerson("", firstName, lastName,shortAddress);
     *
     * @param nino       person NINO
     * @param personFirstName  person first name
     * @param personSecondName person last name
     * @param shortaddress person address
     */
    public void searchPerson(String nino, String personFirstName, String personSecondName, String shortaddress) {
        logger.info("Search for the record, using PersonNINO:" + nino + " PersonFirstName:" + personFirstName + " personSecondName:" + personSecondName);
        closeAllOpenTabs();
        selectOptionFromShortcutsMenu("Clients and Outcomes", "Searches", "Person");
        switchToFrameFromDefault(SearchPersonFrame);
        if (isNotNullOrEmpty(nino)) {
            enterValueInto("Reference", nino);
        } else {
            enterValueInto("First Name", personFirstName);
            enterValueInto("Last Name", personSecondName);
            enterValueInto("Address Line 1",shortaddress);
        }
        waitForCondition(() -> {
            click(personSearchButton);
            return containsElements("table[summary^='Search Results'] tr[data-lix]");
        }, 480, "Person not found in 8 minutes of search");
    }

    /**
     * searches and selects the person record based on reference , first name , last name, shortAddress
     * For Example:
     * selectPersonRecord("", "FirstName", "LastName","shortAddress")   => search by first name and last name
     *
     * @param nino       person NINO
     * @param personFirstName  person first name
     * @param personSecondName person last name
     * @param shortAddress person address
     */
    public void selectPersonRecord(String nino, String personFirstName, String personSecondName, String shortAddress) {
        searchPerson(nino, personFirstName, personSecondName, shortAddress);
        performActionClick(By.cssSelector("table[summary^='Search Results'] tr[data-lix]  .ac"));
        logger.info("Navigate to most recent application");
        waitForPageLoading();
    }

    /**
     * searches the person record based on NINO , first name , last name
     * For Example:
     * searchPerson(personNino, personFirstName, personSecondName)
     * searchPerson("", firstName, lastName);
     *
     * @param nino             person NINO
     * @param personFirstName  person first name
     * @param personSecondName person last name
     */
    public void searchPerson(String nino, String personFirstName, String personSecondName) {
        logger.info("Search for the record, using PersonNINO:" + nino + " PersonFirstName:" + personFirstName + " personSecondName:" + personSecondName);
        closeAllOpenTabs();
        waitForCondition(() -> {
            selectOptionFromShortcutsMenu("Clients and Outcomes", "Searches", "Person");
            return containsElements("iframe[title='Content Panel - Person Search'][src*='Person_search']");
        }, "Person search frame not displayed");
        switchToFrameFromDefault(SearchPersonFrame);
        if (isNotNullOrEmpty(nino)) {
            enterValueInto("Reference", nino);
        } else {
            enterValueInto("First Name", personFirstName);
            enterValueInto("Last Name", personSecondName);

        }
        waitForCondition(() -> {
            jQueryClick("$('div[id*=\"page-action-set-\"] a:contains(\"Search\")')");
            waitForDataDisplay();
            return containsElements("table[summary^='Search Results'] tr[data-lix]");
        }, 660, "Person not found in 8 minutes of search");
    }

    /**
     * selects person record based on NINO
     * For Example:
     * selectPersonRecord(getSharedData().nino)
     *
     * @param personNino person Nino
     */
    public void selectPersonRecord(String personNino) {
        selectPersonRecord(personNino, "", "","");
    }

    /**
     * selects PDC case through the searches menu
     * For Example:
     * selectPDCCase(sharedData.cdpPdcNumber)
     *
     * @param reference provide the PDC Number
     */
    public void selectPDCCase(String reference) {
        logger.info("Search for the pdc case, using reference:" + reference);
        closeAllOpenTabs();
        selectOptionFromShortcutsMenu("Clients and Outcomes", "Searches", "Case");
        switchToFrameByTitle("Case Search");
        By referenceBy = By.cssSelector("input[title='Reference'][data-testid*='Reference']");
        enterText(referenceBy, reference);
        waitForCondition(() -> {
            click(personSearchButton);
            return containsElements("table[summary^='Search Results'] tr[data-lix]");
        }, 360, "Person not found in 6 minutes of search");
        selectRecordFromTable(reference);
        logger.info("Navigate to Pdc case");
    }

    /**
     * Refresh the data table, if the table contains a refresh icon , you can call this method to refresh the records.
     */
    public SPMBasePage refreshPanel() {
        String cssSelector = "a[title=\"Refresh\"],img[alt=\"Refresh\"]";
        logger.debug("click refresh button on the table using: " + cssSelector);
        waitForConditionWithoutException(() -> {
            waitForDataDisplay();
            if (!findElements(By.cssSelector(cssSelector)).isEmpty()) {
                jQueryClick(cssSelector);
                return true;
            }
            return false;
        }, 30, "Failed to click on the element: " + cssSelector);
        return this;
    }


    /**
     * Refreshes the frame that contains the PDC status updates
     */
    public void refreshChallenges() {
        logger.debug("refresh the challenges page to get the update status or details");
        if(!isFrameAlreadyDefault()){
            switchToDefaultFrame();
        }
        clickOnTab("Challenges");
        switchToframeByContentPanelTitle("Content Panel - Challenges");
        refreshPanel();
        switchToDefaultFrame();

    }

    /**
     * Switches to the Evidences section, it first switches to the tab and then to the frame.
     *
     * @param caseType select case type, it only works of person record level and application level
     */
    public void switchToEvidenceSection(CaseType caseType) {
        logger.info("switch to application case Evidence section");
        switch (caseType) {
            case APPLICATIONCASE:
                switchToTab("Evidence").selectSubTab("Evidence");
                switchToFrameFromDefault(applicationCaseEvidenceFrame);
                break;
            case PERSONRECORD:
                switchToTab("Evidence").selectSubTab("Evidence");
                switchToFrameFromDefault(personEvidenceFrame);
                break;
            case PDCCASE:
                switchToTab("Evidence").selectSubTab("Active Evidence");
                switchToFrameFromDefault(pdcEvidenceFrame);
                break;
            default:
                break;
        }
    }

    /**
     * selects the option from the dropdown list based the dropdown field label
     * if you pass empty string it will select the first valid text option [excludes blank value]
     * For leaving the dropdown to blank pass the  option value as "Blank value"
     * For Example:
     * selectValueFromDropdown("Case Participant", caseParticipantName);
     * selectValueFromDropdown("Case Participant", "") => selects first valid value
     * selectValueFromDropdown("Case Participant", "Blank value") => leaves the drop-down value to empty
     *
     * @param label          drop down  field label
     * @param optionToSelect option to select from the drop-down, for first option pass "" and for first available value pass "Blank Value"
     */
    public SPMBasePage selectValueFromDropdown(String label, String optionToSelect) {
        String option = isNullOrEmpty(optionToSelect) ? "" : optionToSelect;
        logger.debug("select option: " + option + "from dropdown: " + label);
        By dropdownInput = By.cssSelector(String.format("input[title*=\"%s\"]", label.replace("'","\\'")));
        String expandButton = format("input[title*=\"%s\"] ~button[title*=\"Open menu\"]", cssEscape(label));
        By expandDropDown = By.cssSelector(expandButton);
        String elementId = getAttribute(dropdownInput,"id");
        By selectOption = By.xpath(String.format("//div[contains(@id,\"downshift\")]/div[contains(text(),\"%1$s\")]", option));
        By selectEquivalentOption = By.xpath(String.format("//div[contains(@id,\"downshift\")]/div[text()=\"%1$s\"]", option));
        if (containsElements(format("$('%1$s')", expandButton))) {
            click(expandDropDown);
            if (isNullOrEmpty(option)) {
                click(By.xpath("(//div[contains(@id,'downshift')]/div/div[text()!=''])[1]"));
                return this;
            }
            else if (option.equals("Other Benefits CFP")) {
                enterText(dropdownInput,"" + Keys.DOWN);
                click(By.xpath(String.format("//div[@id='downshift-0-item-2']")));
                return this;
            }
            else if (option.equals("Blank value")) {
                enterText(dropdownInput,"" + Keys.DOWN);
                click(By.xpath(String.format("//div[@class=\"bx--list-box__menu-item__option\" or @class=\"dijitReset dijitMenuItem\" and contains(@id,\"%1$s\")][text()=\"\"]",elementId)));
                return this;
            }
            if (findElements(selectOption).size() > 1) {
                click(selectEquivalentOption);
            } else {
                click(selectOption);
            }
        } else if (option.equals("Ireland")) {
            enterText(dropdownInput,"" + Keys.DOWN);
            click(By.xpath(String.format("//div[@class=\"bx--list-box__menu-item__option\" or @class=\"dijitReset dijitMenuItem\" and contains(@id,\"%1$s\")][text()=\"%2$s\"]",elementId,  option)));
            return this;
        }else {
            selectValueFromDropDownByIdMap(label, option);
        }
        return this;
    }

    /**
     * selects the value from the dropdown selection, don't make this public. only used for V7 style dropdowns
     *
     * @param label  dropdown label
     * @param option option to select from the dropdown
     */
    private void selectValueFromDropDownByIdMap(String label, String option) {
        By dropdownInput = By.cssSelector(format("input[title*=\"%1$s\"][aria-autocomplete]", cssEscape(label)));
        String dropDownId = getAttribute(dropdownInput, "id");
        By dropDownButton = By.cssSelector(format("div[widgetid='%s'] input", dropDownId));
        By optionToSelect = By.cssSelector(format("div[id*=\"%1$s\"][title*=\"%2$s\"]", dropDownId, option));
        By firstValidOption = By.cssSelector(format("div[id*=\"%1$s\"][item]:not([aria-label])", dropDownId));
        By textBox = By.cssSelector(format("input[title*=\"%1$s\"][value=''],input[title*=\"%1$s\"]", cssEscape(label)));

        try {
            enterText(textBox, option + Keys.DOWN);
            if (isNullOrEmpty(option)) {
                click(firstValidOption);
                return;
            }
            click(optionToSelect);
        } catch (AssertionError | Exception exception) {
            try {
                clickAndWaitForElement(dropDownButton, firstValidOption);
                click(optionToSelect);
            } catch (AssertionError | Exception ex) {
                enterText(textBox, option + Keys.TAB);
            }
        }
    }


    /**
     * Enters the text into the text box using its associated label
     *
     * @param question textbox label, it can be label of text box or textarea
     * @param val      value to enter into the text box or text area
     */
    public void answerQuestionByEnteringTextInInputBox(String question, String val) {
        enterValueInto(question, val);
    }


    /**
     * enable a checkbox where the label appears on the left side of the Checkbox
     */
    public SPMBasePage clickCheckBoxFollowedByText(String textVal) {
        clickCheckBox(textVal);
        return this;
    }

    /**
     * click on the next button and will make sure it enters into the new screen
     * Note: use this method only if the page has h2 tag in that frame
     */
    public void continueToNextPage() {
        logger.debug("click on the next button and make sure it moved to next page");
        waitForDataDisplay();
        String pageSourceBefore = getDriver().getPageSource();
        String query = "var s= false; var selector =document.querySelector(\"a[title*='Click here to submit your answer']\");selector.onclick=function(){s= true};selector.click();return s;";
        Supplier<Boolean> isScreenChanged = () -> (Boolean) evaluateJavascript(query);
        waitForConditionWithoutException(() -> {
            logger.debug("click on next button currentPageTitle:" + getText(pageTitleHeading));
            boolean isPageMoved = isScreenChanged.get() && !getDriver().getPageSource().equals(pageSourceBefore);
            logger.info("Moved to next page: " + isPageMoved);
            return isPageMoved;
        }, 30, "Unable to move to a next page");
    }

    public void continueToNextPageIEG()  {
        waitForDataDisplay();
        if (getText(pageTitleHeading).contains("Correspondence Address Search Result") || getText(pageTitleHeading).contains("Health care professional's address search result"))
        {
            continueToNextPage();
        }
        else
            nextButton.click();
    }

    /**
     * Below method is to click on the Next button in the ApplicationCase modal window
     */
    public void clickNextButton() {
        logger.info("Go to Next Page");
        clickButtonByName("Next");
        waitForDataDisplay();
    }

    /**
     * verifies the text field contains a specific text, works on text fields, dropdowns, text areas
     *
     * @param fieldLabel         field name, it can be a start of the label or end of the label or can be of full label
     * @param expectedFieldValue expected value in the field
     */
    public void textFieldValueShouldContain(String fieldLabel, String expectedFieldValue) {
        By fieldValue = By.cssSelector(String.format("input[title*=\"%1$s\"]", fieldLabel));
        shouldContainValue(fieldLabel + " field value not matched", fieldValue, expectedFieldValue);
    }

    public void sectionFieldValueShouldBe(String fieldLabel, String expectedFieldValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedFieldValue);
        By fieldValue = By.xpath(String.format("//label[contains(text(),\"%1$s\")]/../div", fieldLabel));
        shouldBeEqualToText(fieldLabel + " field value not matched", fieldValue, expectedFieldValue);
    }

    public void sectionFieldValueShouldContain(String fieldLabel, String expectedFieldValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedFieldValue);
        By fieldValue = By.xpath(String.format("//label[contains(text(),\"%1$s\")]/../div", fieldLabel));
        shouldContainText(fieldLabel + " field value not matched", fieldValue, expectedFieldValue);
    }

    /**
     * verifies that field value contains an expected value
     *
     * @param fieldLabel         field name, it can be a start of the label or end of the label or can be of full label
     * @param expectedFieldValue expected value in the field
     */
    public void fieldValueShouldContain(String fieldLabel, String expectedFieldValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedFieldValue);
        By fieldValue = By.xpath(format("//*[contains(text(),\"%1$s\")]/../../div | //*[@class= \"%1$s\"]", fieldLabel));
        shouldContainText(fieldLabel + " field value not matched", fieldValue, expectedFieldValue);
    }
    /**
     * verifies that field value contains an expected value
     *
     * @param fieldLabel         field name, it can be a start of the label or end of the label or can be of full label
     * @param expectedFieldValue expected value in the field
     */
    public void fieldValueShouldBe(String fieldLabel, String expectedFieldValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedFieldValue);
        By fieldValue = By.xpath(String.format("//*[contains(text(),\"%1$s\")]/../../div | //*[@class= \"%1$s\"]", fieldLabel));
        shouldBeEqualToText(fieldLabel + " field value not matched", fieldValue, expectedFieldValue);
    }
    public void contentPanelFieldValueShouldBe(String fieldLabel, String expectedFieldValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedFieldValue);
        String query = format("var filteredListItem = [...document.querySelectorAll('div[class*=\"context-panel-details\"] td,div[class*=\"context-panel-details\"] th')].find(li => li.textContent.trim() === \"%1$s\"); var l=filteredListItem.nextSibling;return l.textContent.trim()",fieldLabel);
        waitForConditionWithoutException(() -> evaluateJavascript(query).toString().contains(expectedFieldValue), 20, "");
        assertThat(fieldLabel + " field value not matched", evaluateJavascript(query).toString().replace("\n", ""), equalTo(expectedFieldValue));
    }
    public void contentPanelFieldValueShouldContain(String fieldLabel, String expectedFieldValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedFieldValue);
        String query = format("var filteredListItem = [...document.querySelectorAll('div[class*=\"context-panel-details\"] td,div[class*=\"context-panel-details\"] th')].find(li => li.textContent.trim() === \"%1$s\"); var l=filteredListItem.nextSibling;return l.textContent.trim()",fieldLabel);
        waitForConditionWithoutException(() -> evaluateJavascript(query).toString().contains(expectedFieldValue), 20, "");
        assertThat(fieldLabel + " field value not matched", evaluateJavascript(query).toString().replace("\n", ""), containsString(expectedFieldValue));
    }

    /**
     * gets the value of the field based on label
     * @param fieldLabel
     * @return
     */
    public String getFieldValue(String fieldLabel) {
        By fieldValue = By.xpath(String.format("//*[contains(text(),\"%1$s\")]/../../div | //*[@class= \"%1$s\"]", fieldLabel));
        return getText(fieldValue);
    }

    /**
     * clicks on the button using name on the button
     *
     * @param name name on the button
     */
    public void clickButtonByName(String name) {
        logger.debug("click on the button using jquery, Name on the Button:" + name);
        waitForDataDisplay();
        String script = String.format("$('span:contains(\"%1$s\"),a:contains(\"%1$s\"),button:contains(\"%1$s\"),button[title*=\"%1$s\"],a[aria-label=\"%1$s\"]')", cssEscape(name));
        jQueryClick(script);
        waitForDataDisplay();
    }

    /**
     * check for error message, if contains error message throws the exception with the error message
     */
    public void checkForErrorMessages() {
        logger.debug("switch to a open model frame and check for the error messages");
        AtomicBoolean isModalWindowExists = new AtomicBoolean(false);
        waitForConditionWithoutException(() -> {
            isModalWindowExists.set(isModalWindowExists());
            return !(isModalWindowExists.get());
        }, 5, "Failed to click on save button");
        if (isModalWindowExists.get()) {
            checkForResolutionElseThrowError();
        }

    }

    /**
     * checks the modal window is launched
     * @return returns true if it's launched otherwise false
     */
    public boolean isModalWindowExists() {
        return containsElements("div[id$='modal-container']");
    }

    /**
     * Below method is to verify the page headers on the ApplicationCase modal windows
     */
    public void verifySPMPageHeader(String textVal) {
        waitForDataDisplay();
        scrollToPageTop();
        shouldContainsToIgnoringCase("Incorrect header title", pageTitleHeading, textVal);
    }

    /**
     * The below method is to click on a radio button by given label text in the ApplicationCase modal window
     */
    public void selectQuestionAnswerRadios(String question, String answer) {
        waitForDataDisplay();
        String radioButton = String.format("$('tr:contains(\"%1$s\") label:contains(\"%2$s\")')", cssEscape(question), cssEscape(answer));
        jQueryClick(radioButton);
    }

    /**
     * clicks on the modal save button and validates the error messages
     * Note: Waits for the modal window to be closed
     */
    public void clickModelSave() {
        clickSaveButton();
        checkForErrorMessages();
    }

    /**
     * switches to the active model window frame
     */
    public void switchToActiveModalDialog() {
        switchToFrameFromDefault(activeModalDialogFrame);
    }

    /**
     * close the all the tabs that are available in tasks section
     */
    public void closeAllOpenTabsInInbox() {
        switchToTab("Inbox");
        waitForCondition(() -> {
            if (containsElements("button[title*='Close - Task']")) {
                Actions action = new Actions(getDriver());
                action.contextClick(getElement(By.cssSelector("button[title*='Close - Task']"))).build().perform();
                click(By.id("curam_widget_MenuItem_3_text"));
                return true;
            }
            return true;
        }, "Failed to close all the open tabs");

    }

    /**
     * This below method confirms if current frame already in default or not. If Frame already a default will return true
     */
    public boolean isFrameAlreadyDefault(){
            if(getDriver().switchTo().defaultContent().getPageSource()!=null)
                return true;
            else
                return false;
    }

    /**
     * Verifies the status of the application, if the expected is not update, it will retry till to the default timeout
     *
     * @param pdcStatus expected status of the pdc application
     */
    public void verifyApplicationStatus(String pdcStatus) {
        logger.info("wait for the expected PDC status and verify");
        By pdcContextPanel = By.cssSelector("iframe[title*='Disability Payment'][page-id='DefaultICProduct_tabDetails'],iframe[page-id='DefaultICProduct_tabDetails']");
        waitForDataDisplay();
        if(!isFrameAlreadyDefault()){
            switchToDefaultFrame();
        }
        if (pdcStatus.equalsIgnoreCase("closed")) {
            switchToFrame(programHeaderFrame);
        } else {
            switchToFrame(pdcContextPanel);
        }
        waitForCondition(() -> {
            refreshChallenges();
            if (pdcStatus.equalsIgnoreCase("closed")) {
                switchToFrame(programHeaderFrame);
            } else {
                switchToFrame(pdcContextPanel);
            }
            waitForDataDisplay();
            return getText(applicationStatus).equalsIgnoreCase(pdcStatus);
        }, 120, "status not updated in the given time, expected:" + pdcStatus + " and actual is :" + getText(applicationStatus));
        shouldBeEqualToText("PDC status is not matched", applicationStatus, pdcStatus);
    }

    /**
     * selects the option from the section tab menu options from the displayed page
     *
     * @param menuOption option to select from the tab widget menu
     */
    public void selectOptionFromDisplayMenu(String menuOption) {
        waitForDataDisplay();
        String tabExpansion = "span[class *='dijitHasDropDownOpen'],span[class *='dijitDropDownButtonOpened']";
        clickAndWaitForElement("span[title=\"Click to display menu\"]:visible,span[title=\"Click to display actions menu\"]", tabExpansion);
        if (isNotNullOrEmpty(menuOption)) {
            jQueryClick(format("table[role=\"menu\"] td:contains(\"%1$s\")", cssEscape(menuOption)));
        }

    }
    public void selectOptionFromMainDisplayMenu(String menuOption){
        switchToDefaultFrame();
        selectOptionFromDisplayMenu(menuOption);
    }


    /**
     * Edits the evidence in the evidence table
     * Note: Before calling this method, you have to be on the right frame Ex: evidence frame
     *
     * @param matchingText Name of the evidence, it can be of multiple partial text, in case of duplicate it selects first matched record
     */
    public void editEvidence(String... matchingText) {
        logger.info("Edit evidence from the evidence table, Evidence - " + Arrays.toString(matchingText));
        actionOnRecord("Edit", matchingText);
    }

    /**
     * adds the proof to the evidence
     *
     * @param matchingText evidence name
     */
    public void addProofToEvidence(String... matchingText) {
        logger.info("Adding proof to the evidence: " + Arrays.toString(matchingText));
        actionOnRecord("Add", matchingText);
        switchToActiveModalDialog();
    }
    /**
     * Edits the specified row in a table
     * @param rowPartialText unique Partial text of the row, in case of duplicate it selects the first
     */
    public void editRowInTable(String rowPartialText) {
        shouldContainRecordRow(rowPartialText);
        actionOnRecord(rowPartialText, "Edit");
    }

    /**
     * performs the task search and select the task using task reference.
     * @param task task reference
     */
    public void searchTask(String task) {
        switchToTab("Inbox");
        selectOptionFromShortcutsMenu("Inbox", "Tasks", "Enhanced Task Search");
        switchToFrameFromDefault(By.cssSelector("iframe[title='Content Panel - Inbox']"));
        enterValueInto("Task ID", task);
        click(personSearchButton);
        String filteredTask = "table[summary *='results'] tr[data-lix] .field>a";
        waitForCondition(() -> {
            boolean isRecordDisplayed = containsElements(filteredTask);
            if (isRecordDisplayed) return true;
            click(personSearchButton);
            return false;
        }, "No pending applications cases to select");
        click(By.cssSelector(filteredTask));

    }

    /**
     * gets the full name based on acronym
     *
     * @param applicationAcronym acronym
     */
    public String getApplicationFullName(String applicationAcronym) {
        Map<String, String> caseNameMap = new HashMap<>();
        caseNameMap.put("BSF", "Best Start Food");
        caseNameMap.put("BSG", "Best Start Grant");
        caseNameMap.put("SCP", "Scottish Child Payment");
        caseNameMap.put("YCG", "Young Carer Grant");
        caseNameMap.put("JSP", "Job Start Payment");
        caseNameMap.put("FSP", "FSP");
        caseNameMap.put("CDP", "Child Disability Payment");
        caseNameMap.put("ADP", "Adult Disability Payment");
        caseNameMap.put("WHP", "Winter Heating Payment");
        caseNameMap.put("CSP", "Carer Support Payment");
        return caseNameMap.getOrDefault(applicationAcronym, applicationAcronym);
    }

    /**
     * gets the full name based on acronym
     *
     * @param applicationAcronym acronym
     */
    public String getFullName(String applicationAcronym) {
        Map<String, String> caseNameMap = new HashMap<>();
        caseNameMap.put("BSF", "Best Start Food");
        caseNameMap.put("BSG", "Best Start Grant");
        caseNameMap.put("SCP", "Scottish Child Payment");
        caseNameMap.put("YCG", "Young Carer Grant");
        caseNameMap.put("JSP", "Job Start Payment");
        caseNameMap.put("FSP", "Funeral Support Payment");
        caseNameMap.put("CDP", "Child Disability Payment");
        caseNameMap.put("ADP", "Adult Disability Payment");
        caseNameMap.put("WHP", "Winter Heating Payment");
        caseNameMap.put("CSP", "Carer Support Payment");
        caseNameMap.put("BSF", "Best Start Food");
        return caseNameMap.get(applicationAcronym);
    }

    /**
     * Checks the status of the checkbox, if checkbox is enabled returns true
     *
     * @param checkBoxLabel checkbox label
     */
    public boolean isCheckBoxEnabled(String checkBoxLabel) {
        logger.debug("check the status of the checkbox:" + checkBoxLabel);
        waitForDataDisplay();
        String Jquery = String.format("return $('input[aria-label *=\"%1$s\"],input[title^=\"%1$s\"]').length>0", cssEscape(checkBoxLabel) );
        waitForCondition(() -> (Boolean) evaluateJavascript(Jquery), "check box not present");
        String checkBoxStatus = String.format("return $('input[aria-label^=\"%1$s\"]:checked,input[title^=\"%1$s\"]:checked').length>0", cssEscape(checkBoxLabel));
        return (boolean) evaluateJavascript(checkBoxStatus);
    }

    /**
     * Enables the checkbox based on the checkbox label
     *
     * @param checkBoxLabel checkbox label
     */
    public void enableCheckBox(String checkBoxLabel) {
        if (!isCheckBoxEnabled(checkBoxLabel)) {
            logger.debug("Enable the checkbox:" + checkBoxLabel);
            jQueryClick(String.format("input[title^=\"%1$s\"] +label,input[title$=\"%1$s\"] +label", cssEscape(checkBoxLabel)));
        }
    }

    /**
     * Enables or disables the checkBox that are available in section
     *
     * @param section       section header
     * @param checkBoxLabel label of the checkBox to enable
     */
    public void enableCheckBox(String section, String checkBoxLabel, boolean enableCheckBox) {
        isCheckBoxEnabled(checkBoxLabel);//wait and check at least one matching checkbox is available--> dummy check
        boolean isCheckBoxEnabled = (boolean) evaluateJavascript("return $('section:contains(\"%1$s\") input[aria-label^=\"%2$s\"]:checked').length>0", section, checkBoxLabel);
        String elementToClick = format("$('section:contains(\"%1$s\") input[title^=\"%2$s\"] +label')", section, checkBoxLabel);
        logger.debug("Enable the" + checkBoxLabel + " checkbox:" + enableCheckBox);
        if (enableCheckBox) {
            if (!isCheckBoxEnabled) jQueryClick(elementToClick);
        } else {
            if (isCheckBoxEnabled) jQueryClick(elementToClick);
        }
    }

    /**
     * Disable the checkbox based on the checkbox label
     *
     * @param checkBoxLabel checkbox label
     */
    public void disableCheckBox(String checkBoxLabel) {
        if (isCheckBoxEnabled(checkBoxLabel)) {
            logger.debug("Disable the checkbox:" + checkBoxLabel);
            click(By.cssSelector(String.format("input[title^='%1$s'] +label,input[title$='%1$s'] +label", checkBoxLabel)));
        }
    }

    /**
     * This method to be used for all tyoes of ID & V selection across the program
     *
     * @param section         - Tells about under which category the selection to be made
     * @param checkboxToClick - Tells about which item to be selected
     */
    public void selectCheckBoxUnderSection(String section, String checkboxToClick) {
        jQueryClick(String.format("$('section:contains(\"%1$s\") input[title*=\"%2$s\"] +label')", cssEscape(section) , cssEscape(checkboxToClick)));
    }

    /**
     * Clicks on the checkbox
     *
     * @param label checkbox label
     */
    public void clickCheckBox(String label) {
        String formattedLabel = cssEscape(label);
        try {
            jQueryClick(String.format("$('tr:contains(\"%1$s\") label[title*=\"%1$s\"]')", formattedLabel));
        } catch (Exception e) {
            jQueryClick(String.format("$('tr:contains(\"%s\") label[class^=\"checkbox-touchable-area\"]')", formattedLabel));
        }
    }

    /**
     * Use this method to click on any buttons appearing on Modal pages. Example: Edit/ADD Evidence modal pages
     */
    public void clickModelButton(String... buttonName) {
        logger.debug("switch to default frame and click on the modal window button, Button Name :" + buttonName);
        switchToDefaultFrame();
        String buttonToClick = buttonName.length==1?buttonName[0]:buttonName[1];
        String formatedQuery = format("div[data-dojo-attach-point=\"modalFooter\"] button:contains(\"%1$s\")", cssEscape(buttonToClick));
        for (String button : buttonName) {
            if (button.equals(buttonName[0])) continue;
            formatedQuery += format(", div[data-dojo-attach-point=\"modalFooter\"] button:contains(\"%1$s\")", cssEscape(button));
        }
        logger.debug("switch to default frame and click on the modal window button, Button Name :" + formatedQuery);
        String filteredQuery = format( "var element = $('%1$s').filter(function() {return $(this).text().trim() === \"%2$s\";}).first();element.click();",formatedQuery,cssEscape(buttonToClick));
        evaluateJavascript(filteredQuery);
        waitForDataDisplay();
    }

    public void clickModelButtonIEG(String buttonName) {
        switchToDefaultFrame();
        String xpath = String.format("//button[contains(text(), '%1$s')]", buttonName);
        WebElement modelButton = getDriver().findElement(By.xpath(xpath));
        modelButton.click();
        waitForDataDisplay();
    }

    /**
     * Waits for the records to be appeared in table, if records are not shown in the given time it throws the exception
     * Note: Switch to the table before the call of this method
     */
    public void waitForRecordsToAppearInTable() {
        logger.debug("wait for the records to appear in the table");
        waitForConditionWithoutException(() -> {
            if (!containsElements("tr[data-lix]")) refreshPanel();
            return containsElements("tr[data-lix]");
        }, 30, "Records not found in the table");
    }
    /**
     * Waits for the records to be appeared in table, if records are not shown in the given time it throws the exception
     * Note: Switch to the table before the call of this method
     */
    public void waitForRecordsToAppearInTable(String record,int time) {
        logger.debug("wait for the records to appear in the table");
        waitForConditionWithoutException(() -> {
            if (isRecordExist(record)) return true;
            refreshPanel();
            return false;
        }, time, "Records not found in the table");
    }

    /**
     * finds the matching record based on the search criteria and selects the specified option from the menu
     *
     * @param matchingText    matching text on the record, it can be of multiple text or empty string if you want to select first record
     * @param actionToPerform second matching text on the record
     */
    public void actionOnRecord(String actionToPerform, String... matchingText) {
        String matchingRow = getFormattedRowMatchingQuery(matchingText);
        logger.info("perform requested action on the record that contains text:" + matchingRow + "\t Action to perform:" + actionToPerform);
        String clickMenu = format("%s span[title*=\"Click to display\"]", matchingRow);
        logger.debug("edit query : " + clickMenu);
        waitForDataDisplay();
        waitForPageToBeLoaded();
        logger.info("waitForPageToBeLoaded");
        String tabExpansion = format("table[role='menu'] td:contains('%s')", cssEscape(actionToPerform));
        clickAndWaitForElement(clickMenu, tabExpansion);
        logger.info("clickAndWaitForElement");
        selectMenuOption(actionToPerform);
        logger.info("selectMenuOption");
        waitForDataDisplay();
    }


    /**
     * selects the options from the widget menu
     *
     * @param optionName item to select from the widget menu, if possible try with the first word
     */
    public void selectMenuOption(String optionName) {
        jQueryClick(format("$('table[role=\"menu\"] td:contains(\"%s\"):visible').first()", cssEscape(optionName)));
    }

    /**
     * finds the record with the matching text and verifies the expected text on that record
     *
     * @param expectedMultiText expected text to be appeared on the record
     */
    public SPMBasePage shouldContainRecord(String... expectedMultiText) {
        waitForRecordsToAppearInTable();
        String recordToMatch = format("$('%s')", getFormattedRowMatchingQuery(expectedMultiText));
        logger.info("search for the record that contains the matching text:" + recordToMatch);
        assertTrue("Record not exist in the table, with the matching text query" + recordToMatch, containsElements(recordToMatch));
        return this;
    }

    /**
     Returns a formatted CSS selector for locating a table row based on
     the specified text query. The method concatenates a list of strings into a CSS selector,
     ensuring that each string is properly escaped to prevent injection attacks.
     @param expectedMultiText The list of strings to match against the row in the HTML table.
     @return A CSS selector string that matches the specified text query.
     @throws NullPointerException if any of the expectedMultiText elements is null.
     */
    public SPMBasePage shouldContainRecordRow(int count, String... expectedMultiText) {
        waitForRecordsToAppearInTable();
        String recordToMatch = format("return $('%s').length", getFormattedRowMatchingQuery(expectedMultiText));
        logger.info("search for the record that contains the matching text:" + recordToMatch + " " + "and count equals to : " + count);
        assertThat("Record not exist in the table or count not matched, with the matching text query" + " " + recordToMatch + " count:" + count, Integer.valueOf(evaluateJavascript(recordToMatch).toString()), equalTo(count));
        return this;
    }

    /**
     * Verifies that the table does not contain a record with the specified multi-text values.
     *
     * @param expectedMultiText an array of multi-text values to check for
     * @return the current page object instance for chaining method calls
     * @throws AssertionError if the table contains a record with the specified multi-text values
     */
    public SPMBasePage shouldNotContainRecord(String... expectedMultiText) {
        waitForRecordsToAppearInTable();
        String recordToMatch = format("$('%s')", getFormattedRowMatchingQuery(expectedMultiText));
        logger.info("search for the record that contains the matching text:" + recordToMatch);
        assertTrue("Record exist in the table, with the matching text query" + recordToMatch, !containsElements(recordToMatch));
        return this;
    }


    @NotNull
    public String getFormattedRowMatchingQuery(String... expectedMultiText) {
        StringBuilder recordToMatch = new StringBuilder("tr[data-lix]");
        for (String expectedText : expectedMultiText) {
            if (isNotNullOrEmpty(expectedText)) {
                recordToMatch.append(format(":contains(\"%s\")", cssEscape(expectedText)));
            }
        }
        return recordToMatch.toString();
    }

        /**
         * Purpose: To be globally used to take a screenshot of any SPM page
         * Method Name:takeScreenshot
         * @author:Zak
         */
        public void takeScreenshot(){
            logger.info("taking screenshot of current open page ");
            Serenity.takeScreenshot();
        }

    /**
     * checks the record exists in the table
     *
     * @param textOnRecord text on the record, can be of multiple text
     */
    public boolean isRecordExist(String... textOnRecord) {
        waitForDataDisplay();
        logger.info("verify the existence of the record:" + Arrays.toString(textOnRecord));
        String matchedRecord = format("$('%s')", getFormattedRowMatchingQuery(textOnRecord));
        return containsElements(matchedRecord);
    }

    public void navigateToMyWorkQueues(){
        switchToTab("Inbox");
        selectOptionFromShortcutsMenu("Inbox", "Work Queues", "My Work Queues");
    }
    public String getReference(String firstName, String lastName) {
        logger.info("get the NINO reference of the person having firstName:" + firstName + " and lastName:" + lastName);
        searchPerson("", firstName, lastName,"");
        String reference = getText(By.xpath(format("(//a[contains(text(),'%1$s') and @href])[last()]", firstName + " " + lastName)))
                .split("-")[1].trim();
        return reference;
    }

    /**
     * selects the record from the table(clicks on the first anchor tag)
     *
     * @param matchingText matching text, can be of multiple text. if empty selects the first record
     */
    public void selectRecordFromTable(String... matchingText) {
        waitForDataDisplay();
        String matchingRecord = getFormattedRowMatchingQuery(matchingText);
        logger.info("find the matching record" + matchingRecord + " and select the anchor tag that contains a matching text" + false);
        String matchedRecord = format("$('%s a[href]:visible')", matchingRecord);
        jQueryClick(matchedRecord);
        waitForDataDisplay();
    }

    /**
     * selects the record from the table(clicks on the first anchor tag)
     *
     * @param matchingText matching text, can be of multiple text. if empty selects the first record
     */
    public void selectSpecificRecordFromTable(String recordToSelect,String... matchingText) {
        waitForDataDisplay();
        String matchingRecord = getFormattedRowMatchingQuery(matchingText);
        logger.info("find the matching record" + matchingRecord + " and select the anchor tag that contains a matching text" + false);
        String matchedRecord = format("$('%1$s a[href]:contains(\"%2$s\")')", matchingRecord,recordToSelect);
        jQueryClick(matchedRecord);
        waitForDataDisplay();
    }

    public SPMBasePage shouldContainRecordRow(String... expectedMultiText) {
        waitForRecordsToAppearInTable();
        String recordToMatch = format("$('%s')", getFormattedRowMatchingQuery(expectedMultiText));
        logger.info("search for the record that contains the matching text:" + recordToMatch);
        assertTrue("Record not exist in the table, with the matching text query" + recordToMatch, containsElements(recordToMatch));
        return this;
    }


    /**
     * expands the record for more details
     *
     * @param matchingText pass the matching text on the row to expand
     */
    public void toggleRecord(String... matchingText) {
        waitForDataDisplay();
        String row = getFormattedRowMatchingQuery(matchingText);
        String matchedRecord = format("$('%s a[title=\"Toggle\"]')",  row);
        logger.info("Expands or toggle the record:" + matchedRecord);
        try {
            jQueryClick(matchedRecord);
        } catch (Exception exception) {
            Assert.fail("No matching record found to toggle: " + matchedRecord + "\n" + exception.getMessage());
        }
        waitForDataDisplay();
    }

    /**
     * navigates to the  pages until it found the matched record
     *
     * @param refreshTable if it is set true it will refresh the table and search
     * @param matchingText search the data table using the text on the record
     */
    public void searchRecordUsingPagination(boolean refreshTable, String... matchingText) {
        String recordToFind = format("$('%s')", getFormattedRowMatchingQuery(matchingText));
        logger.info("search the pages using the pagination, record to search:" + recordToFind + " is refresh required:" + refreshTable);
        waitForDataDisplay();
        String paginationCSS = "select[title='Page size']";
        String nextPage = "img[alt='Next page']";
        waitForCondition(() -> {
            if (refreshTable) refreshPanel();
            if (containsElements(paginationCSS)) {
                int totalRecordCount = Integer.parseInt(getText(By.cssSelector("#ROW_INFO P")).split("out of ")[1].replace("]", ""));
                setPagination("45");
                if (containsElements(recordToFind)) return true;
                double size = totalRecordCount / 45.0;
                if (size > 1) {
                    for (int i = 0; i < size; i++) {
                        if (containsElements(recordToFind)) return true;
                        if (containsElements(nextPage)) {
                            click(By.cssSelector(nextPage));
                        }
                    }
                } else {
                    refreshPanel();
                    return false;
                }
            } else {
                if (!containsElements(recordToFind)) {
                    refreshPanel();
                    return false;
                }
            }
        return containsElements(recordToFind);
    },420,"Unable to find the record:"+recordToFind);
}

    /**
     * Set Pagination to display number of the records
     *
     * @param num Number of records to display
     */
    public void setPagination(String num) {
        logger.debug("set pagination limit to : " + num);
        String paginationCSS = "select[title='Page size']";
        waitForCondition(() -> {
            if (containsElements(paginationCSS)) {
                selectDropdownByValue(getElement(cssEscape(paginationCSS)), num);
            }
            return true;
        }, 30, "Unable to set to required pagination count:" + num);
    }

    /**
     * switches to the modal frame
     * it switches to which evidence modal, edit or add new
     */
    public void switchToEvidenceFrameModelByName(String evidenceName) {
        waitForDataDisplay();
        By evidenceModalFrame = By.cssSelector(format("iframe[title*='%s']", evidenceName));
        logger.info("Attempting to switch to Iframe - " + evidenceModalFrame);
        switchToFrameFromDefault(evidenceModalFrame);
    }

    /**
     * In order to use the method, the page object class should inherit from CommonEvidenceObjects
     * The below method should be used from Step Definitions. No need to write separate methods for each and every switch to a different frame
     * Frame Type: Modal Frame
     */
    public void switchToframeByActionTypeAndEvidenceName(String ActionType, String EvidenceName) {
        waitForDataDisplay();
        switchToFrameFromDefault(By.xpath("//iframe[contains(@title,'Modal Frame') and contains(@title,'" + ActionType + "') and contains(@title,'" + EvidenceName + "')]"));
    }


    /**
     * Purpose: To Switch to a Content Panel By its Title Name
     * Frame Type: Content Panel
     */
    public void switchToframeByContentPanelTitle(String ContentPanelTitle) {
        switchToFrameByTitle(ContentPanelTitle);
    }

    /**
     * captures the SPM calendar date and stores it into the shared data
     */
    public void captureCalendarDate() {
        switchToTab("Calendar");
        click(calendarView);
        switchToFrame(calendarFrame);
        click(calenderGoTodayButton);
        waitForDataDisplay();
        sharedData.spmCalendarDate = getAttribute(calendarSpmDate, "value");
        logger.info("SPM Calendar Date: " + sharedData.spmCalendarDate);
    }

    /**
     * logout the user from the SPM, it will handle logouts anywhere from the page
     */
    public void logoutUser() {
        logger.info("Log out from the SPM application");
        switchToDefaultFrame();
        jQueryClick("$('tr[title*=\"Log\"]')");
        performActionClick(logoutFinal);
    }

    public void selectChangeReasonDropdown(String dropDown) {
        selectValueFromDropdown("Change Reason", dropDown);
    }

    /**
     * Purpose: This Common method Handles all type of Input values in the Edit Evidence Modal
     * Types include: dropdown,textbox,date,textarea,checkbox
     */
    public void FillAnswer_Evidence_Modal(String identifier, String data, String field_type) {
        logger.debug("update the field type :" + field_type + " label: " + identifier + "with value :" + data);
        switch (field_type.toLowerCase()) {
            case "dropdown":
                selectValueFromDropdown(identifier, data);
                return;
            case "paralleldropdown":
                List<WebElementFacade> listBoxes = findAll(String.format("input[title^=\"%s\"]", identifier));
                for (int i = 0; i < listBoxes.size(); i++) {
                    selectValueFromDropdown(getAttribute(listBoxes.get(i), "title"), data.split(":")[i]);
                }
                break;

            case "textbox":
            case "textarea":
                enterValueInto(identifier, data);
                break;
            case "date":
                String formatted_date;
                if (data.contains("SPM Calendar Date")) {
                    formatted_date = DateHelper.getRelativeDateFromAnyDay(getSharedData().spmCalendarDate, data, "dd/MM/yyyy");
                } else {
                    formatted_date = DateHelper.getRelativeDateFromToday(data, "dd/MM/yyyy");
                }
                setDateField(identifier, formatted_date);
                break;
            case "checkbox":
                enableCheckBox(identifier);
                break;
        }
    }


    public void vefifyFieldValue(Map<String, String> eligibilitySummary) {
        for (String eligibility : eligibilitySummary.keySet()) {
            fieldValueShouldContain(eligibility, eligibilitySummary.get(eligibility));
        }
    }

    /**
     * checks the eligibility status of the record
     *
     * @param eligibilityStatus expected eligibility status
     */
    public void checkEligibilityStatus(String eligibilityStatus) {
        logger.debug("check eligibility status , expected:" + eligibilityStatus);
        switchToTab("Eligibility Checks");
        switchToFrameByTitle("Eligibility Checks");
        waitForRecordsToAppearInTable();
        shouldBeEqualToText("the case decision displayed as  ", caseEligibilityDecision, eligibilityStatus);
    }

    /**
     * adds the new evidence to the existing evidence list in application case
     *
     * @param evidenceName evidence to add into the application case evidences
     */
    public void addNewEvidence(String evidenceName) {
        logger.debug("add new evidence:" + evidenceName);
        if (!evidenceName.equals("CWHA Decision Evidence")) {
            switchToTab("Evidence");
        }
        switchToFrameByTitle("Evidence");
        if (containsElements("a[title='New']")) {
            clickLinkAndWaitForModalFrame("New", "Evidence");
        } else {
            selectOptionFromDisplayMenu("New");
        }
        switchToActiveModalDialog();
        switchToFrameByTitle("New Evidence");
        waitForCondition(() -> {
            actionOnRecord("Add", evidenceName);
            switchToDefaultFrame();
            boolean isNewEvidenceWindowOpened = !findElements(By.cssSelector(format("iframe[title*='%s']", evidenceName))).isEmpty();
            if (!isNewEvidenceWindowOpened) {
                switchToActiveModalDialog();
                return false;
            }
            return true;
        }, "failed to open the new evidence:" + evidenceName);
        switchToEvidenceFrameModelByName("New " + evidenceName);
    }

    /**
     * verifies the evidences present in evidence section and also validates the count of evidences
     * it works for both person level and application level
     *
     * @param evidences        evidences to validate
     * @param timeOutInSeconds within how much time we are expecting the evidence to available
     */
    public void verifyEvidencesAndCount(List<Map<String, String>> evidences, int timeOutInSeconds) {
        logger.debug("verify evidence and count");
        Map<String, String> expectedEvidences = new HashMap<>();
        for (Map<String, String> evidence : evidences) {
            Object[] keys = (evidence.keySet()).toArray();
            expectedEvidences.put(evidence.get(keys[0]), evidence.get(keys[1]));
        }
        if (containsElements("*[title='Issues or Verifications exist']")) {
            verifyRecordCount(expectedEvidences, 3, timeOutInSeconds);
        } else {
            verifyRecordCount(expectedEvidences, 2, timeOutInSeconds);
        }
    }

    public Integer getRecordCountByColumnFilter(String textOnRecord, int columnToFilterIndex) {
        waitForDataDisplay();
        logger.info("verify the existence of the record:" + textOnRecord);
        List<String> evidence = getTextOfAllElements(format("tr[data-lix]>td:nth-child(%1$s)", columnToFilterIndex));
        int recordCount = (int) evidence.stream().filter(evi -> evi.equals(textOnRecord)).count();
        return recordCount;
    }

    /**
     * verify the records and count of the records in table
     *
     * @param expectedRecords  matching text of the record
     * @param columnIndex      On which column number we want to verify
     * @param timeOutInSeconds how much should wait for the records to appear, timeout in seconds
     */
    public void verifyRecordCount(Map<String, String> expectedRecords, int columnIndex, int timeOutInSeconds) {
        logger.debug("verify the record count");
        for (String evidence : expectedRecords.keySet()) {
            waitForRecordsToAppearInTable(evidence,30);
            waitForCondition(() -> {
                        boolean status = getRecordCountByColumnFilter(evidence,columnIndex) == Integer.parseInt(expectedRecords.get(evidence));
                        if (status) return true;
                        refreshPanel();
                        return false;
                    },timeOutInSeconds,
                    format("evidence count not matched for %1$s: Actual:%2$s, Expected:%3$s", evidence, getRecordCountByColumnFilter(evidence,columnIndex), expectedRecords.get(evidence)));
        }
    }

    public void assertErrorForProofsOutstandingAndClickCancel(String errorMessage) {
        switchToActiveModalDialog();
        shouldContainText("Error message not matched", proofsOutstandingErrorMessage, errorMessage);
        clickModelButton("Cancel");
    }

    /**
     * runs the eligibility check
     */
    public void runEligibilityCheck() {
        logger.info("Run the eligibility checks");
        switchToTab("Eligibility Checks");
        clickLinkAndWaitForModalFrame("Check Eligibility", "Eligibility Checks");
        switchToActiveModalDialog();
        clickModelButton("Yes");
        checkForErrorMessages();
        waitForPageLoaded();
    }

    /**
     * clicks on the element and waits for the modal window to be launched
     *
     * @param cssSelector jquery/ css selector / Query selector of the element, it will work for all the combinations
     */
    public void clickAndWaitForModalFrame(String cssSelector, String frameToSwitch) {
        waitForCondition(() -> {
            switchToFrameByTitle(frameToSwitch);
            click(By.cssSelector(cssSelector));
            switchToDefaultFrame();
            return !findElements(By.cssSelector("iframe[title^='Modal Frame']")).isEmpty();
        }, "expected frame not displayed, clicked on  element:" + cssSelector);
    }

    /**
     * clicks on the anchor element that contains the passed text and waits for the Modal window to be launched
     *
     * @param textOnLink text present on the anchor element
     */
    public void clickLinkAndWaitForModalFrame(String textOnLink, String frameToSwitch) {
        logger.debug("click on the anchor tag element and wait for the modal window to launch, link button:" + textOnLink);
        clickAndWaitForModalFrame(format("a[title^=\"%1$s\"]", textOnLink), frameToSwitch);
    }

    /**
     * verifies the error message displayed on the page, Note: if it is frame make sure you're on the correct frame
     *
     * @param textOnErrorMessage expected error message, verify using contains
     */
    public void verifyErrorMessage(String textOnErrorMessage) {
        logger.debug("verify the error message displayed on the frame, expected error message:" + textOnErrorMessage);
        shouldContainText("Error message not matched: ", By.cssSelector("*[id $='error-messages']"), textOnErrorMessage);
    }

    public void waitForDataDisplay() {
        logger.debug("check for message please wait...");
        waitForConditionWithoutException(() -> !containsElements("div[title^='Please wait...']"), 120, "Page took longer to load");
    }

    public void goToLastPage() {
        if (containsElements("a[title='Last page']")) click(By.cssSelector("a[title=\"Last page\"]"));
    }
    /**
     * Use this method to click on any buttons appearing on Modal pages. Example: Edit/ADD Evidence modal pages
     */
    public void clickbutton(String Button) {
        switchToDefaultFrame();
        String xpath = "//div[@data-dojo-attach-point=\"modalFooter\" and starts-with(@id,\"curam_modal_CuramCarbonModal\")]//button[text()=\"" + Button + "\"]";
        click(By.xpath(xpath));
    }

    /**
     * @param by     element that you'd like to check the colour of
     * @param colour rgb colour you'd like to check is correct
     *               <p>
     *               Use this method to validate that correct colour is displayed by an element
     */
    public void elementShouldContainColour(By by, String colour) {
        waitForConditionWithoutException(() -> getAttribute(by, "style").contains(colour), 20, "");
        String actualValue = getAttribute(by, colour);
        Assertions.assertThat(actualValue).describedAs("element colour not matched" + " Actual: '%s', Expected: '%s'", actualValue, colour).contains(colour);
    }

    public void searchDocument(String option) {
        logger.info("Search for the document, using DocumentName:" +option);
        By FromDate = By.xpath("//input[@data-testid='date_Field.Label.FromDate']");
        By ToDate = By.xpath("//input[@data-testid='date_Field.Label.ToDate']");

        closeAllOpenTabs();
        selectOptionFromShortcutsMenu("Clients and Outcomes", "Documents", "Available Documents");
        switchToFrameFromDefault(SearchDocumentFrame);
        switch (option) {

            case "":
                enterValueInto("Reference", option);
            break;

            case "DocReferenceNumber":
                enterValueInto("Reference",sharedData.captureGroupId.get(0));
                break;

            case "Nino":
                try{
                    enterText(FromDate, DateHelper.returnFormattedDate(sharedData.contentReceiptDate, "yyyy-MM-dd", "dd/MM/yyyy"));
                    enterText(ToDate, DateHelper.getRelativeDatefromDate(DateHelper.returnFormattedDate(sharedData.contentReceiptDate, "yyyy-MM-dd", "dd/MM/yyyy"),0, 0,0, 6));
                } catch(ParseException e) {
                    logger.error("Parse Error :" + e);
                    logger.info("Defaulting to standard date range");
                    enterText(FromDate,getRelativeDate("-6").format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
                    enterText(ToDate,getRelativeDate("0").format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
                }
                enterValueInto("National Insurance Number",sharedData.nino);
                break;
            case "PersonalIdentifiers":
                try{
                    enterText(FromDate, DateHelper.returnFormattedDate(sharedData.contentReceiptDate, "yyyy-MM-dd", "dd/MM/yyyy"));
                    enterText(ToDate, DateHelper.getRelativeDatefromDate(DateHelper.returnFormattedDate(sharedData.contentReceiptDate, "yyyy-MM-dd", "dd/MM/yyyy"),0, 0,0, 6));
                } catch(ParseException e) {
                    logger.error("Parse Error :" + e);
                    logger.info("Defaulting to standard date range");
                    enterText(FromDate,getRelativeDate("-6").format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
                    enterText(ToDate,getRelativeDate("0").format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
                }
                enterValueInto("First Name", sharedData.firstName);
                enterValueInto("Post Code",sharedData.postcode);
                break;
            case "Names":
                try{
                    enterText(FromDate, DateHelper.returnFormattedDate(sharedData.contentReceiptDate, "yyyy-MM-dd", "dd/MM/yyyy"));
                    enterText(ToDate, DateHelper.getRelativeDatefromDate(DateHelper.returnFormattedDate(sharedData.contentReceiptDate, "yyyy-MM-dd", "dd/MM/yyyy"),0, 0,0, 6));
                } catch(ParseException e) {
                    logger.error("Parse Error :" + e);
                    logger.info("Defaulting to standard date range");
                    enterText(FromDate,getRelativeDate("-6").format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
                    enterText(ToDate,getRelativeDate("0").format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
                }
                enterValueInto("First Name", sharedData.firstName.substring(0,3));
                enterValueInto("Last Name",sharedData.lastName.substring(sharedData.lastName.length() -3));
        }

        click(personSearchButton);
    }

    public void verifyDocumentDetails() throws Exception{
        String dob;
        dob = DateHelper.returnFormattedDate(sharedData.clientDateofbirth.toString(), "yyyy-MM-dd", "dd/MM/yyyy");
        switchToFrameFromDefault(SearchDocumentFrame);
        shouldContainRecordRow(getSharedData().nino, sharedData.firstName + " " + sharedData.lastName,dob,"Un Resolved");

    }
    public void verifyDocumentDetails(String staus) throws Exception{
        switchToFrameFromDefault(SearchDocumentFrame);
        shouldContainRecordRow(getSharedData().nino, sharedData.firstName + " " + sharedData.lastName,sharedData.dob,staus);

    }

    public void EmptyDocSearchErrorMessage(List<Map<String, String>> errorMessages) {
        switchToframeByContentPanelTitle("Content Panel - Document List (messages present)");
        if (containsElements("#ieg-error-messages,#error-messages")) {
            for (Map<String, String> message : errorMessages) {
                List<String> extractedTextList = getTextOfAllElements("ul[id='error-messages'] div +div");
                String item = message.get("error message");
                Assert.assertTrue(item + " is NOT in outstanding items to verify", extractedTextList.toString().contains(item));
            }
        }

    }

    public String pageTitle(){
        String nameOfPage;
        waitForPageLoaded();
        return getDriver().getTitle();

    }
    public void clickSaveNextButton() {
        logger.info("switch to default frame and click on save button");
        clickModelButton("Save & Next");
        clickModelButton("Finish");
    }

    /** A method to check that a table has the correct headers.
     *
     * @param expectedMultiText a list of header names to test
     * @return current page object instance for chaining method calls
     */
    public SPMBasePage tableShouldContainHeaders(String... expectedMultiText) {
        String recordToMatch = format("$('%s')", getFormattedHeaderMatchingQuery(expectedMultiText));
        assertThat("Headers not matched in the table with the matching text query " + recordToMatch, containsElements(recordToMatch));
        return this;
    }

    /**
     * verifies that field value should be equals to ignoring case expected value
     *
     * @param fieldLabel    field name, it can be a start of the label or end of the label or can be of full label
     * @param expectedValue expected value in the field
     */
    public void labelValueShouldBeEqualToIgnoringCase(String fieldLabel, String expectedValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedValue);
        By fieldValue = By.xpath(String.format("//label[contains(text(),\"%1$s\")]/../div", fieldLabel));
        shouldBeEqualToIgnoringCase(fieldLabel + " field value not matched", fieldValue, expectedValue);
    }

    @NotNull
    public String getFormattedHeaderMatchingQuery(String... expectedMultiText) {
        StringBuilder recordToMatch = new StringBuilder("th[class*=\"field\"]");
        for (String expectedText : expectedMultiText) {
            if (isNotNullOrEmpty(expectedText)) {
                recordToMatch.append(format(":contains(\"%s\")", expectedText));
            }
        }
        return recordToMatch.toString();
    }

    public void labelValueShouldBe(String fieldLabel, String expectedValue) {
        logger.debug("verify the field value , field label:" + fieldLabel + " expected value:" + expectedValue);
        By fieldValue = By.xpath(String.format("//label[contains(text(),\"%1$s\")]/../div", fieldLabel));
        shouldBeEqualToText(fieldLabel + " field value not matched", fieldValue, expectedValue);
    }

}

```
